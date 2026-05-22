# API Básica con FastAPI

Proyecto básico desarrollado con **FastAPI**, un framework moderno de Python para crear APIs rápidas, simples y con documentación automática.

## Requisitos

- Python 3.9 o superior
- pip
- Git
- Cuenta en GitHub
- Cuenta en Railway

## Estructura del proyecto

```text
proyecto_fastapi/
│
├── main.py
├── requirements.txt
├── railway.json
└── README.md
```

## Código principal

Archivo `main.py`:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def inicio():
    return {"mensaje": "Hola desde FastAPI"}

@app.get("/saludo/{nombre}")
def saludar(nombre: str):
    return {"mensaje": f"Hola {nombre}"}
```

## Dependencias

Archivo `requirements.txt`:

```txt
fastapi
uvicorn
```

## Ejecutar en local

### 1. Crear entorno virtual

```bash
python -m venv venv
```

### 2. Activar entorno virtual

En Windows:

```bash
venv\Scripts\activate
```

En Linux o macOS:

```bash
source venv/bin/activate
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

### 4. Ejecutar el servidor

```bash
uvicorn main:app --reload
```

### 5. Abrir en el navegador

API:

```text
http://127.0.0.1:8000
```

Documentación Swagger:

```text
http://127.0.0.1:8000/docs
```

Documentación ReDoc:

```text
http://127.0.0.1:8000/redoc
```

## Despliegue en Railway

### 1. Crear archivo `railway.json`

```json
{
  "$schema": "https://railway.app/railway.schema.json",
  "build": {
    "builder": "NIXPACKS"
  },
  "deploy": {
    "startCommand": "uvicorn main:app --host 0.0.0.0 --port $PORT"
  }
}
```

### 2. Subir el proyecto a GitHub

```bash
git init
git add .
git commit -m "Proyecto FastAPI básico"
```

Agregar el repositorio remoto:

```bash
git remote add origin URL_DEL_REPOSITORIO
git branch -M main
git push -u origin main
```

### 3. Crear proyecto en Railway

1. Ingresar a Railway.
2. Crear un nuevo proyecto.
3. Seleccionar **Deploy from GitHub Repo**.
4. Escoger el repositorio del proyecto.
5. Railway instalará las dependencias y ejecutará la API.

### 4. Generar dominio público

En Railway:

```text
Settings > Networking > Generate Domain
```

Ejemplo de URL final:

```text
https://mi-api.up.railway.app
```

### 5. Probar la API desplegada

API:

```text
https://mi-api.up.railway.app
```

Documentación:

```text
https://mi-api.up.railway.app/docs
```

## Rutas disponibles

| Método | Ruta | Descripción |
|---|---|---|
| GET | `/` | Mensaje inicial |
| GET | `/saludo/{nombre}` | Saludo personalizado |

## Conclusión

Este proyecto muestra una implementación básica de FastAPI, incluyendo su ejecución local y su despliegue en Railway mediante GitHub.
