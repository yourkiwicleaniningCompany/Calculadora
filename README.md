<!DOCTYPE html>
<html>

<head>
    <title>Calculadora de Limpieza</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
        integrity="sha512-9usAa10IRO0HhonpyAIVpjrylPvoDwiPUiKdWk5t3PyolY1cOd4DSE0Ga+ri4AuTroPR5aQvXU9xC6qOPnzFeg=="
        crossorigin="anonymous" referrerpolicy="no-referrer" />
    <style>
        /* --- CSS Integrado --- */
        *,
        *:before,
        *:after {
            margin: 0;
            box-sizing: border-box;
        }

        /* --- Estilos generales del body --- */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            /* Tipo de letra moderno */
            color: #343a40;
            /* Gris oscuro para mejor legibilidad */
            background-color: #f8f9fa;
            /* Gris claro de fondo */
            margin: 0;
        }

        /* --- Estilos del encabezado --- */
        h1 {
            margin: 0 0 20px 0;
            text-align: center;
            font-size: 2.2em;
            color: #070707;
            /* Azul primario para resaltar */
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
            /* Sombra sutil */
        }

        /* --- Estilos del formulario --- */
        form {
            max-width: 95%;
            margin: 20px auto;
            padding: 25px;
            border-radius: 15px;
            gap: 20px;
            background-color: #fff;
            /* Fondo blanco para el formulario */
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
            /* Sombra suave */
        }

        /* --- Estilos de las etiquetas (labels) --- */
        label {
            display: block;
            padding-left: 8px;
            font-size: 1em;
            color: #495057;
            /* Gris más claro para las etiquetas */
            margin-bottom: 8px;
        }

        /* --- Estilos de los campos de entrada (input, select, textarea) --- */
        input[type="number"],
        input[type="email"],
        select,
        textarea {
            display: block;
            width: 100%;
            height: 45px;
            /* Aumentado la altura para facilitar el toque */
            padding-left: 15px;
            padding-right: 15px;
            font-size: 1em;
            border-radius: 25px;
            border: 1px solid #ced4da;
            /* Borde sutil */
            transition: border-color 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
            /* Transiciones suaves */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #495057;
            box-sizing: border-box;
        }

        input:focus,
        select:focus,
        textarea:focus {
            outline: none;
            border-color: #80bdff;
            /* Azul más claro al enfocar */
            box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
            /* Sombra de enfoque */
        }

        /* --- Estilos específicos del textarea --- */
        textarea {
            height: 150px;
            /* Restaurado la altura original */
            resize: vertical;
            padding-top: 10px;
        }

        /* --- Estilos del botón --- */
        button {
            width: 100%;
            /* Botón ocupa todo el ancho */
            max-width: 250px;
            /* Ancho máximo para que no se vea demasiado grande en pantallas grandes */
            height: 50px;
            position: relative;
            display: block;
            margin: 20px auto;
            border-radius: 25px;
            border: none;
            background-color: #007bff;
            /* Azul primario */
            color: white;
            font-size: 1.1em;
            transition: background-color 0.3s ease;
            cursor: pointer;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
            /* Sombra suave */
        }

        button:hover {
            background-color: #0056b3;
            /* Azul más oscuro al pasar el ratón */
        }

        /* --- Estilos de la sección de resultados --- */
        #resultados {
            display: none;
            text-align: center;
            font-size: 1.1em;
            margin-top: 25px;
            padding: 15px;
            border-radius: 10px;
            background-color: #e9ecef;
            /* Gris muy claro */
        }

        #resultados span {
            font-weight: bold;
            color: #007bff;
        }

        /* --- Estilos para los descuentos --- */
        .descuento-container {
            display: none;
        }

        .descuento-opcion {
            display: none;
        }

        /* --- Estilos para los extras --- */
        .extra-item {
            margin-bottom: 5px;
        }

        /* --- Estilos para agregar extras --- */
        #agregarExtraContainer {
            display: flex;
            flex-direction: column;
            align-items: stretch;
            margin-bottom: 15px;
        }

        #agregarExtraContainer label {
            width: auto;
            margin-right: 0;
            text-align: left;
            margin-bottom: 8px;
        }

        #agregarExtraContainer input[type="text"],
        #agregarExtraContainer input[type="number"] {
            width: 100%;
            box-sizing: border-box;
            border-radius: 25px;
            margin-bottom: 12px;
            height: 40px;
            /* Aumentado la altura */
        }

        #agregarExtraContainer button {
            width: 100%;
            box-sizing: border-box;
            border-radius: 25px;
            height: 45px;
            font-size: 1em;
            background-color: #28a745;
            /* Verde */
            transition: background-color 0.3s ease;
        }

        #agregarExtraContainer button:hover {
            background-color: #218838;
            /* Verde más oscuro al pasar el ratón */
        }

        /* --- Estilos para la lista de extras --- */
        #extrasContainer {
            margin-top: 15px;
        }

        #extrasContainer ul {
            list-style-type: none;
            padding: 0;
        }

        #extrasContainer li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
            padding: 12px;
            background-color: #f1f3f5;
            /* Gris muy claro */
            border-radius: 10px;
        }

        #extrasContainer li input[type="checkbox"] {
            width: 20px;
            height: 20px;
            margin-right: 10px;
            transform: scale(1.2);
        }

        #extrasContainer li label {
            margin: 0;
            padding: 0;
            font-size: 1em;
        }

        #extrasContainer li .delete-extra {
            background: none;
            border: none;
            color: #dc3545;
            /* Rojo */
            cursor: pointer;
            font-size: 1.2em;
            padding: 0;
            transition: color 0.3s ease;
        }

        #extrasContainer li .delete-extra:hover {
            color: #c82333;
            /* Rojo más oscuro al pasar el ratón */
        }

        /* --- Estilos para el colapsable --- */
        .collapsible {
            background-color: #6c757d;
            /* Gris medio */
            color: white;
            cursor: pointer;
            padding: 15px;
            width: 100%;
            border: none;
            text-align: left;
            outline: none;
            font-size: 1em;
            border-radius: 10px;
            margin-bottom: 10px;
            transition: background-color 0.3s ease;
        }

        .collapsible:hover {
            background-color: #5a6268;
            /* Gris más oscuro al pasar el ratón */
        }

        .collapsible:after {
            content: '\f107';
            font-family: FontAwesome;
            float: right;
            margin-left: 5px;
        }

        .collapsible.active {
            background-color: #5a6268;
        }

        .collapsible.active:after {
            content: "\f106";
        }

        .content {
            padding: 15px;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out;
            background-color: #f8f9fa;
            border-radius: 10px;
        }

        /* --- Estilos para el contenedor de resultados --- */
        .results-container {
            max-width: 95%;
            margin: 25px auto;
            padding: 20px;
            border-radius: 15px;
            gap: 20px;
            background-color: #f8f9fa;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        /* --- Media query para pantallas más grandes --- */
        @media (min-width: 768px) {
            h1 {
                font-size: 2.8em;
                /* Restaurar tamaño de fuente original */
            }

            form {
                max-width: 700px;
                padding: 35px;
                gap: 30px;
            }

            label {
                font-size: 1.1em;
                padding-left: 12px;
                margin-bottom: 10px;
            }

            input[type="number"],
            input[type="email"],
            select,
            textarea {
                height: 50px;
                /* Restaurar altura original */
                font-size: 1.1em;
                border-radius: 30px;
                padding-left: 18px;
                padding-right: 18px;
                margin: 12px;
            }

            textarea {
                height: 180px;
            }

            button {
                height: 55px;
                font-size: 1.2em;
                border-radius: 30px;
                margin: 30px auto;
                padding: 12px 25px;
                max-width: 300px;
            }

            #resultados {
                font-size: 1.2em;
                margin-top: 30px;
            }

            #agregarExtraContainer {
                flex-direction: row;
                align-items: center;
            }

            #agregarExtraContainer label {
                width: auto;
                margin-right: 10px;
                margin-bottom: 0;
            }

            #agregarExtraContainer input[type="text"],
            #agregarExtraContainer input[type="number"] {
                width: 30%;
                border-radius: 30px;
                margin-bottom: 0;
            }

            #agregarExtraContainer button {
                width: 20%;
                border-radius: 30px;
            }

            .results-container {
                max-width: 600px;
                margin: 30px auto;
                padding: 25px;
                gap: 30px;
            }
        }
    </style>
</head>

<body>
    <h1>Calculadora De Limpieza</h1>

    <form id="myForm">
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>

        <!-- Cleaning Form -->
        <label for="tipoLimpieza">Tipo de Limpieza:</label>
        <select id="tipoLimpieza" name="tipoLimpieza" onchange="mostrarDescuentosFrecuencia()">
            <option value=""></option>
            <option value="standard">Standard</option>
            <option value="deep">Deep</option>
            <option value="move">Move</option>
        </select>

        <div id="frecuenciaContainer" style="display:none;">
            <label for="frecuencia">Frecuencia:</label>
            <select id="frecuencia" name="frecuencia">
                <option value="unico">Único</option>
                <option value="semanal">Semanal</option>
                <option value="quincenal">Quincenal</option>
                <option value="mensual">Mensual</option>
            </select>
        </div>

        <div id="descuentoSemanalContainer" class="descuento-container">
            <label for="descuentoSemanal">Descuento Semanal (%):</label>
            <input type="number" id="descuentoSemanal" name="descuentoSemanal" value="20">
        </div>

        <div id="descuentoQuincenalContainer" class="descuento-container">
            <label for="descuentoQuincenal">Descuento Quincenal (%):</label>
            <input type="number" id="descuentoQuincenal" name="descuentoQuincenal" value="15">
        </div>

        <div id="descuentoMensualContainer" class="descuentoMensualContainer descuento-container">
            <label for="descuentoMensual">Descuento Mensual (%):</label>
            <input type="number" id="descuentoMensual" name="descuentoMensual" value="5">
        </div>

        <label for="piesCuadrados">Pies Cuadrados:</label>
        <input type="number" id="piesCuadrados" name="piesCuadrados" required>

        <label for="tarifaHora">Tarifa por Hora:</label>
        <input type="number" id="tarifaHora" name="tarifaHora" required>

        <label for="numEmpleados">Número de Empleados Para El Trabajo:</label>
        <input type="number" id="numEmpleados" name="numEmpleados" required>

        <label for="taxes">Impuestos Sobre La Venta (%):</label>
        <input type="number" id="taxes" name="taxes" value="0" onchange="saveTaxes()">

        <div id="descuentoPromocionalContainer">
            <div id="descuentoPromocionalTipoContainer">
                <label> Descuento Promocional:</label>
                <select id="descuentoPromocionalTipo" name="descuentoPromocionalTipo"
                    onchange="mostrarOpcionesDescuento();">
                    <option value="moneda">Moneda ($)</option>
                    <option value="porcentaje">Porcentaje (%)</option>
                </select>
            </div>

            <div id="descuentoMonedaContainer" class="descuento-opcion">
                <label for="descuentoMoneda">Descuento:</label>
                <input type="number" id="descuentoMoneda" name="descuentoMoneda" value="0">
            </div>

            <div id="descuentoPorcentajeContainer" class="descuento-opcion">
                <label for="descuentoPorcentaje">Descuento:</label>
                <input type="number" id="descuentoPorcentaje" name="descuentoPorcentaje" value="0">
            </div>
        </div>

        <h2>Extras:</h2>
        <button type="button" class="collapsible">Mostrar/Ocultar Extras</button>
        <div class="content">
            <div id="extrasContainer">
                <ul id="extras-list">
                </ul>
            </div>
        </div>
        <div id="agregarExtraContainer">
            <label for="extraNombre">Nombre:</label>
            <input type="text" id="extraNombre" name="extraNombre">
            <label for="extraPrecio">Precio:</label>
            <input type="number" id="extraPrecio" name="extraPrecio" value="0">
            <button type="button" onclick="agregarExtra()">Agregar</button>
        </div>

        <div id="resultados" class="results-container">
        </div>

        <button type="button" onclick="calcularPrecio(event)">Calcular</button>
    </form>

    <script>
        let extras = []; // Array to hold extra items
        const scriptURL = "https://script.google.com/macros/s/AKfycbw45tuqbBrrdBVm2omkU_AbA5z1kyAkdwLf-aZX05zKAKaL-Bqu7s9p90gR8OKEDAuH/exec"; //CAMBIAR

        function mostrarOcultarElemento(id, mostrar) {
            const elemento = document.getElementById(id);
            if (elemento) {
                elemento.style.display = mostrar ? "block" : "none";
            }
        }

        function mostrarDescuentosFrecuencia() {
            const tipoLimpieza = document.getElementById("tipoLimpieza").value;
            const esDeep = tipoLimpieza === "deep";

            mostrarOcultarElemento("descuentoSemanalContainer", esDeep);
            mostrarOcultarElemento("descuentoQuincenalContainer", esDeep);
            mostrarOcultarElemento("descuentoMensualContainer", esDeep);
        }

        function mostrarOpcionesDescuento() {
            const tipoDescuento = document.getElementById("descuentoPromocionalTipo").value;

            if (tipoDescuento === "moneda") {
                mostrarOcultarElemento("descuentoMonedaContainer", true);
                mostrarOcultarElemento("descuentoPorcentajeContainer", false);
            } else {
                mostrarOcultarElemento("descuentoMonedaContainer", false);
                mostrarOcultarElemento("descuentoPorcentajeContainer", true);
            }
        }

        document.getElementById('tipoLimpieza').addEventListener('change', function() {
            const frecuenciaContainer = document.getElementById('frecuenciaContainer');
            const tipoLimpieza = this.value;

            if (tipoLimpieza === 'standard') {
                frecuenciaContainer.style.display = 'block';
            } else {
                frecuenciaContainer.style.display = 'none';
            }
        });

        function agregarExtra() {
            const extraNombre = document.getElementById("extraNombre").value;
            const extraPrecio = parseFloat(document.getElementById("extraPrecio").value);

            if (extraNombre && !isNaN(extraPrecio)) {
                const extraId = "extra" + Date.now();
                const newExtra = {
                    id: extraId,
                    nombre: extraNombre,
                    precio: extraPrecio,
                    checked: false // default to unchecked
                };

                extras.push(newExtra);
                updateExtrasList();

                document.getElementById("extraNombre").value = "";
                document.getElementById("extraPrecio").value = "0";
            } else {
                alert("Por favor, ingresa un nombre y un precio válidos para el extra.");
            }
        }

        function eliminarExtra(extraId) {
            extras = extras.filter(extra => extra.id !== extraId);
            updateExtrasList();
        }

        function toggleExtra(extraId) {
            extras = extras.map(extra => {
                if (extra.id === extraId) {
                    extra.checked = !extra.checked;
                }
                return extra;
            });
            updateExtrasList();
        }

        function updateExtrasList() {
            const extrasList = document.getElementById("extras-list");
            extrasList.innerHTML = ""; // Clear existing list

            extras.forEach(extra => {
                const listItem = document.createElement("li");
                const checkboxId = `checkbox-${extra.id}`;

                listItem.id = `extraItem-${extra.id}`;
                listItem.innerHTML = `
                    <input type="checkbox" id="${checkboxId}" ${extra.checked ? 'checked' : ''} onchange="toggleExtra('${extra.id}')">
                    <label for="${checkboxId}">${extra.nombre} ($${extra.precio.toFixed(2)})</label>
                    <button type="button" class="delete-extra" onclick="eliminarExtra('${extra.id}')">
                        <i class="fas fa-trash-alt"></i>
                    </button>
                `;
                extrasList.appendChild(listItem);
            });
            localStorage.setItem('extras', JSON.stringify(extras)); // Save extras to localStorage
        }

        function loadExtras() {
            const storedExtras = localStorage.getItem('extras');
            if (storedExtras) {
                extras = JSON.parse(storedExtras);
                updateExtrasList();
            }
        }

        function saveTaxes() {
            const taxesValue = document.getElementById('taxes').value;
            localStorage.setItem('taxes', taxesValue);
        }

        function loadTaxes() {
            const storedTaxes = localStorage.getItem('taxes');
            if (storedTaxes) {
                document.getElementById('taxes').value = storedTaxes;
            }
        }

        function formatTime(minutes) {
            const hours = Math.floor(minutes / 60);
            const remainingMinutes = minutes % 60;
            return `${hours} horas y ${remainingMinutes} minutos`;
        }

        window.onload = () => {
            loadExtras(); // Load extras on page load
            loadTaxes(); // Load taxes on page load

            // Establecer valores por defecto al cargar la página
            document.getElementById("descuentoSemanal").value = 40;
            document.getElementById("descuentoQuincenal").value = 30;
            document.getElementById("descuentoMensual").value = 10;

            var coll = document.getElementsByClassName("collapsible");
            var i;

            for (i = 0; i < coll.length; i++) {
                coll[i].addEventListener("click", function() {
                    this.classList.toggle("active");
                    var content = this.nextElementSibling;
                    if (content.style.maxHeight) {
                        content.style.maxHeight = null;
                    } else {
                        content.style.maxHeight = content.scrollHeight + "px";
                    }
                });
            }
        };

        async function calcularPrecio(event) {
            event.preventDefault(); // Prevent the default form submission

            let precioBase = 0;
            let tiempoEstimado = 0;
            let precioTotal = 0;
            let taxesValue = 0;
            let precioExtras = 0;

            const email = document.getElementById("email").value; // Obtiene el email
            const tipoLimpieza = document.getElementById("tipoLimpieza").value;
            const frecuencia = document.getElementById("frecuencia").value;
            const piesCuadrados = parseFloat(document.getElementById("piesCuadrados").value);
            const tarifaHora = parseFloat(document.getElementById("tarifaHora").value);
            const numEmpleados = parseInt(document.getElementById("numEmpleados").value);
            const taxes = parseFloat(document.getElementById("taxes").value);
            const descuentoMoneda = parseFloat(document.getElementById("descuentoMoneda").value);
            const descuentoPorcentaje = parseFloat(document.getElementById("descuentoPorcentaje").value);
            const descuentoSemanal = parseFloat(document.getElementById("descuentoSemanal").value);
            const descuentoQuincenal = parseFloat(document.getElementById("descuentoQuincenal").value);
            const descuentoMensual = parseFloat(document.getElementById("descuentoMensual").value);
            const descuentoPromocionalTipo = document.getElementById("descuentoPromocionalTipo").value;

            extras.forEach(extra => {
                if (extra.checked) {
                    precioExtras += extra.precio;
                }
            });

            const resultadosDiv = document.getElementById("resultados");
            resultadosDiv.className = "results-container";

            if (tipoLimpieza === "deep") {
                 precioBase = (piesCuadrados / 300) * tarifaHora; // Tasa Deep

                // Calcula el precio con la fórmula de Deep + descuento semanal
                const deepSemanal = precioBase * (1 - (descuentoSemanal / 100));

                // Calcula el precio con la fórmula de Deep + descuento quincenal
                const deepQuincenal = precioBase * (1 - (descuentoQuincenal / 100));

               // Calcula el precio con la fórmula de Deep + descuento mensual
                const deepMensual = precioBase * (1 - (descuentoMensual / 100));

                precioTotal = precioBase + precioExtras;
                taxesValue = precioTotal * (taxes / 100);
                precioTotal += taxesValue;
                precioTotal -= descuentoMoneda;
                precioTotal *= (1 - descuentoPorcentaje / 100);

                resultadosDiv.innerHTML = `
                    <label>Precio Base:</label>
                    <span>$${precioBase.toFixed(2)}</span><br><br>

                    <label>Impuestos:</label>
                    <span>$${taxesValue.toFixed(2)}</span><br><br>

                    <label>Precio Final :</label>
                    <span>$${precioTotal.toFixed(2)}</span><br><br>

                    <label>Precio Semanal:</label>
                    <span>$${deepSemanal.toFixed(2)}</span><br><br>

                    <label>Precio Quincenal:</label>
                    <span>$${deepQuincenal.toFixed(2)}</span><br><br>

                    <label>Precio Mensual:</label>
                    <span>$${deepMensual.toFixed(2)}</span>
                `;

            } else if (tipoLimpieza === "standard") {
                precioBase = (piesCuadrados / 500) * tarifaHora;
                const descuentoFrecuencia = frecuencia === 'semanal' ? 0.20 : frecuencia === 'quincenal' ? 0.15 : frecuencia === 'mensual' ? 0.05 : 0;
                tiempoEstimado = Math.round((piesCuadrados / 500) / numEmpleados / (5 / 60)) * 5;

                precioTotal = precioBase * (1 - descuentoFrecuencia) + precioExtras;
                taxesValue = precioTotal * (taxes / 100);
                precioTotal += taxesValue;
                precioTotal -= descuentoMoneda;
                precioTotal *= (1 - descuentoPorcentaje / 100);

                let descuentoFrecuenciaTexto = "";
                if (frecuencia === 'semanal') {
                    descuentoFrecuenciaTexto = "Semanal (20%)";
                } else if (frecuencia === 'quincenal') {
                    descuentoFrecuenciaTexto = "Quincenal (15%)";
                } else if (frecuencia === 'mensual') {
                    descuentoFrecuenciaTexto = "Mensual (5%)";
                } else {
                    descuentoFrecuenciaTexto = "Ninguno";
                }

                resultadosDiv.innerHTML = `
                    <label>Precio Base:</label>
                    <span>$${precioBase.toFixed(2)}</span><br><br>

                    <label>Impuestos:</label>
                    <span>$${taxesValue.toFixed(2)}</span><br><br>
                    <label>Tiempo Estimado:</label>
                    <span>${formatTime(tiempoEstimado)}</span><br><br>

                    <label>Descuento por Frecuencia:</label>
                    <span>${descuentoFrecuenciaTexto}</span><br><br>

                    <label>Precio Standard:</label>
                    <span>$${precioTotal.toFixed(2)}</span>
                `;

            } else { // move
                precioBase = (piesCuadrados / 250) * tarifaHora;
                precioTotal = precioBase + precioExtras;
                taxesValue = precioTotal * (taxes / 100);
                precioTotal += taxesValue;
                precioTotal -= descuentoMoneda;
                precioTotal *= (1 - descuentoPorcentaje / 100);

                tiempoEstimado = Math.round((piesCuadrados / 250) / numEmpleados / (5 / 60)) * 5;

                resultadosDiv.innerHTML = `
                    <label>Precio Base:</label>
                    <span>$${precioBase.toFixed(2)}</span><br><br>

                    <label>Impuestos:</label>
                    <span>$${taxesValue.toFixed(2)}</span><br><br>

                    <label>Precio Move:</label>
                    <span>$${precioTotal.toFixed(2)}</span>
                    <label>Tiempo Estimado:</label>
                    <span>${formatTime(tiempoEstimado)}</span>
                `;
            }

            resultadosDiv.style.display = "block"; // Ensure it's visible

            // Data to send to Google Sheets - SOLO EMAIL
            const data = {
                email: email
                // Eliminamos toda la otra información
            };

            try {
                const response = await fetch(scriptURL, {
                    method: 'POST',
                    mode: 'no-cors', // Important for Google Sheets Script to work without CORS issues
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(data),
                });

                // Check if the request was successful (status in the range 200-299)
                if (response.ok) {
                    console.log('Email enviado correctamente a Google Sheets');
                } else {
                    console.error('Error al enviar el email a Google Sheets:', response.status, response.statusText);
                }
            } catch (error) {
                console.error('Error al enviar el email a Google Sheets:', error);
            }
        }
    </script>
</body>

</html>
