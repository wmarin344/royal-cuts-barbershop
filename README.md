# Royal Cuts Barbershop

Sitio web responsivo para una barbería, con un flujo completo de reservación, cancelación y reagendamiento de citas. Sin backend propio: la disponibilidad en tiempo real se resuelve con Firebase Firestore y las notificaciones automáticas por correo con EmailJS.

## Demo en vivo

[Ver sitio](https://TU-LINK-DE-NETLIFY.netlify.app)

## Características

- **Reserva de citas** en varios pasos: selección de servicio, barbero, fecha y hora, y datos del cliente.
- **Calendario de disponibilidad en tiempo real**, conectado a Firebase Firestore: los horarios ya reservados se bloquean automáticamente para el resto de los clientes.
- **Gestión de citas** mediante un ID único generado al reservar (`gestionar-cita.html`): el cliente puede cancelar o reagendar su cita sin necesidad de crear una cuenta.
- **Notificaciones automáticas por correo** (EmailJS) en cada evento: nueva reserva, cancelación y reagendamiento, tanto para el cliente como para el dueño del negocio.
- **Diseño responsivo**, adaptado a dispositivos móviles y de escritorio.

## Tecnologías

- HTML, CSS, JavaScript (sin frameworks)
- Firebase Firestore (base de datos en tiempo real para disponibilidad de citas)
- EmailJS (envío de correos desde el frontend, sin backend propio)

## Estructura del proyecto

```
RoyalCuts/
├── index.html              # Página principal
├── reserva.html             # Flujo de reservación de citas
├── confirmacion.html        # Resumen de la cita confirmada
├── gestionar-cita.html      # Cancelar / reagendar una cita existente
├── css/
│   ├── style.css             # Estilos globales
│   ├── indexStyle.css        # Estilos de index.html
│   ├── reservaStyle.css      # Estilos de reserva.html
│   ├── confirmacionStyle.css # Estilos de confirmacion.html
│   └── gestionStyle.css      # Estilos de gestionar-cita.html
└── assets/                   # Imágenes y logo
```

## Cómo correrlo localmente

Al ser un proyecto 100% frontend (sin backend propio), no requiere instalación de dependencias ni servidor. Basta con:

1. Clonar el repositorio:

```bash
git clone https://github.com/wmarin344/royal-cuts-barbershop.git
```

2. Abrir `index.html` directamente en el navegador, o servirlo con cualquier servidor estático (por ejemplo, la extensión "Live Server" de VS Code).

## Notas técnicas

- Las credenciales de Firebase y EmailJS visibles en el código (`firebaseConfig`, Public Key, Service/Template ID) están pensadas para exponerse del lado del cliente; la seguridad real se controla con las Reglas de Seguridad de Firestore y la restricción de dominio en EmailJS, no ocultando estos valores.
- Al no existir un backend propio, no hay una validación atómica de disponibilidad en el instante exacto de confirmar una cita: existe una ventana breve en la que, en teoría, dos personas podrían intentar reservar el mismo horario casi al mismo tiempo.
