# 🤖 BuilderBot x Chatwoot Gateway

![Dashboard Preview](./src/assets/image.png)

Una solución completa para conectar **WhatsApp** (vía Baileys) con **Chatwoot** utilizando **BuilderBot**. Este proyecto actúa como un middleware que permite gestionar conversaciones de WhatsApp directamente desde la interfaz de agentes de Chatwoot, con soporte total para archivos multimedia y una interfaz gráfica de configuración.

## ✨ Características Principales

- **Panel de Configuración Visual:** Interfaz web (`/v1/chatwoot`) para conectar tu instancia sin tocar código.
- **Soporte Multimedia Completo:**
  - 🗣️ **Notas de Voz:** Se envían como adjuntos a Chatwoot.
  - 📸 **Imágenes y Videos:** Reenvío automático con detección de tipos MIME.
  - 📄 **Documentos:** Soporte para PDFs y otros archivos.
  - 📍 **Ubicación:** Convierte las coordenadas de WhatsApp en enlaces de Google Maps.
- **Persistencia Local:** La configuración se guarda en un archivo JSON local, facilitando el reinicio.
- **Webhook Automático:** Endpoint dedicado para recibir respuestas desde Chatwoot hacia WhatsApp.


## 🛠️ Requisitos Previos

- **Node.js** (v18 o superior)
- **pnpm** (Gestor de paquetes recomendado)
- Una instancia de **Chatwoot** activa.
- Un dispositivo móvil con WhatsApp listo para escanear.

## 🚀 Instalación y Puesta en Marcha

1. **Clonar el repositorio:**
   ```
   git clone <URL_DE_TU_REPO>
   cd <NOMBRE_DE_TU_CARPETA>
   ```
2. **Instalar dependencias:** Se recomienda usar pnpm para una instalación rápida y eficiente.
 ```
 pnpm install axios
 ```
3. **Iniciar el Bot**.
 ```
 pnpm start
 ```



```markdown
## ⚙️ Configuración Paso a Paso

Este bot incluye un dashboard visual para facilitar la integración.

### 1. Acceder al Panel
Abre tu navegador y ve a:
`{host}}/v1/chatwoot`

### 2. Tarjeta "Conexión Chatwoot"
Ingresa los datos de tu instancia de Chatwoot:
- **URL Instance:** La dirección de tu Chatwoot (ej: `https://app.chatwoot.com`).
- **Phone:** El número de teléfono (identificador del contacto).
- **Account ID:** El ID numérico de tu cuenta.
- **Inbox ID:** El ID de tu bandeja de entrada tipo "API".
- **Access Token:** Tu token personal de usuario (*Profile Settings -> Access Token*).

> Haz clic en **"Conectar & Guardar"**.

### 3. Tarjeta "Integración"
- **Webhook:** Copia la URL generada (ej: `.../v1/messages`) y pégala en la configuración de tu Inbox en Chatwoot.
- **Código QR:** Haz clic en el botón verde **"Abrir Código QR"** para escanear y vincular tu WhatsApp.


## 📂 Estructura del Proyecto

- `app.js`: Punto de entrada y lógica de flujos (Bienvenida, Media, Audio, etc.).
- `public/front/chatwoot.html`: Interfaz gráfica de configuración.
- `public/json/currentKeys.json`: Archivo donde se guardan las credenciales (generado automáticamente).
- `src/assets/`: Carpeta temporal para descargas multimedia.

## 📡 Endpoints de la API

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/v1/chatwoot` | Panel de configuración visual. |
| `GET` | `/v1/get-chatwoot-config` | Obtiene la configuración guardada. |
| `POST` | `/v1/save-chatwoot-config` | Guarda las credenciales de Chatwoot. |
| `POST` | `/v1/messages` | Webhook para recibir mensajes de Chatwoot. |
| `GET` | `/` | Muestra el QR de Baileys. |

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**.