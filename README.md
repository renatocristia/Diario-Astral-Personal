# Diario-Astral-Personal

🌙 Diario Astral Personal
Sumativa 2 — Desarrollo de Aplicación Web con JavaScript

Aplicación web para registrar reflexiones astrales diarias, con gestión dinámica del DOM, validaciones avanzadas y estructuras de datos eficientes.
git rebase -i --rootFuncionalidades

Formulario con validaciones avanzadas — nombre (RegExp), fecha (no futura), signo, energía, reflexión (longitud) y estado de ánimo (interactivo)
Manipulación dinámica del DOM — agregar, renderizar y eliminar entradas sin recargar la página
Filtros por signo zodiacal — generados dinámicamente según los datos existentes
Estadísticas en tiempo real — total de entradas, signo más frecuente y energía dominante
Persistencia con localStorage — las entradas se mantienen entre sesiones
Prevención de XSS — uso exclusivo de textContent y createElement; función escaparHTML y sanitizarTexto
Diseño responsive — estética pastel con tipografía editorial


🛠️ Tecnologías

HTML5 semántico
CSS3 (Grid, Custom Properties, animaciones)
JavaScript ES6+ (sin frameworks)


📁 Estructura del proyecto
diario-astral/
├── index.html       # App principal (HTML + CSS + JS en un archivo)
└── README.md        # Documentación

🔐 Seguridad y buenas prácticas
PrácticaImplementaciónPrevención XSSescaparHTML() + sanitizarTexto() con createTextNodeSin innerHTML peligrosoTodo el DOM se construye con createElementValidación RegExp/^[a-zA-ZáéíóúÁÉÍÓÚüÜñÑ\s]{2,50}$/ para nombreValidación semánticaFecha no futura, selects obligatorios, largo de textoDatos tipadosObjetos con estructura fija antes de guardarse

🧩 Funciones reutilizables
jsescaparHTML(str)        // Escapa caracteres peligrosos → previene XSS
sanitizarTexto(str)     // Elimina HTML usando createTextNode
generarId()             // ID único por timestamp + random
validarNombre(v)        // RegExp nombre válido
validarFecha(v)         // Fecha real y no futura
validarSelect(v)        // Select no vacío
validarReflexion(v)     // Longitud entre 10–400 chars
marcarCampo(...)        // Muestra/oculta error visual en campo
mostrarToast(msg)       // Notificación flotante temporal
crearTarjetaEntrada(e)  // Construye tarjeta DOM segura desde objeto
renderizarLista()       // Renderiza entradas filtradas y ordenadas
filtrarEntradas(arr, f) // Filtra por signo o devuelve todos
actualizarFiltros()     // Genera botones de filtro dinámicamente
actualizarStats()       // Calcula y muestra estadísticas
agregarEntrada(datos)   // Agrega al array y actualiza toda la UI
eliminarEntrada(id)     // Filtra el array y actualiza la UI
guardarEntradas()       // Persiste en localStorage (con try/catch)
cargarEntradas()        // Recupera desde localStorage

🤖 Uso de IA
Herramienta utilizada
Claude (Anthropic) + GitHub Copilot

Prompt enviado a la IA

"Tengo una app de diario astral en JavaScript. Necesito funciones de validación robusta para: un campo de nombre (solo letras y tildes), una fecha que no sea futura, y una reflexión con mínimo 10 y máximo 400 caracteres. También necesito una función para sanitizar texto del usuario antes de renderizarlo en el DOM, sin usar innerHTML, para prevenir ataques XSS. Devuelve las funciones limpias y reutilizables."


Mejora aplicada
La IA generó el esqueleto de las funciones validarNombre, validarFecha, sanitizarTexto y escaparHTML. A partir de eso:

Se adoptó el patrón de createTextNode dentro de sanitizarTexto — más seguro que limpiar con RegExp directamente.
Se refinó la RegExp de nombre para incluir todos los caracteres acentuados del español: [a-zA-ZáéíóúÁÉÍÓÚüÜñÑ\s]
Se refactorizó marcarCampo para que fuera un helper genérico reutilizable en todos los campos, en lugar de duplicar lógica campo por campo.
Se aplicó la sugerencia de envolver localStorage en try/catch para manejar cuotas excedidas silenciosamente.


Reflexión sobre el uso de IA
La integración de IA fue útil para acelerar la etapa de validaciones y seguridad, que suelen ser repetitivas. Sin embargo, el diseño de la arquitectura general (arreglo de objetos, flujo de renderizado, estructura de funciones) fue desarrollado manualmente para asegurar coherencia y comprensión del código.

🚀 Despliegue

Subir index.html y README.md a un repositorio GitHub
Activar GitHub Pages desde Settings → Pages → Branch: main
La app estará disponible en https://usuario.github.io/diario-astral/


👥 Integrantes
NombreRol[Nombre 1]Desarrollo JS + Validaciones[Nombre 2]UI/UX + README + Informe IA