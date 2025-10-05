# PostgreSQL con Persistencia

Este proyecto configura un contenedor Docker con PostgreSQL y persistencia de datos.

## Requisitos Previos

- Docker y Docker Compose instalados

## Configuración

### 1. Crear archivo de variables de entorno

Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

```env
DB_NAME=ventas
DB_USER=admin
DB_PASSWORD=contraseña_secreta
DB_PORT=5432
DB_INTERNAL_PORT=5432
```

> **Nota:** Modifica estos valores según tus necesidades de seguridad y configuración.

### 2. Ejecutar contenedor

```bash
docker compose up -d
```

Para verificar que el contenedor está ejecutándose:

```bash
docker compose ps
```

Para detener el contenedor:

```bash
docker compose down
```

## Conexión a la Base de Datos

Una vez que el contenedor esté ejecutándose, puedes conectarte usando cualquier cliente de PostgreSQL como DBeaver, pgAdmin, TablePlus, o la línea de comandos.

### Parámetros de Conexión

- **Host:** `localhost`
- **Puerto:** `5432` (o el valor configurado en `DB_PORT`)
- **Base de datos:** `ventas` (o el valor configurado en `DB_NAME`)
- **Usuario:** `admin` (o el valor configurado en `DB_USER`)
- **Contraseña:** El valor configurado en `DB_PASSWORD`

### Ejemplo con DBeaver

A continuación se muestra un ejemplo de configuración de conexión usando DBeaver:

![Ejemplo de conexión con DBeaver](https://i.imgur.com/2GXN0G1.png)

### Conexión por línea de comandos

También puedes conectarte usando `psql`:

```bash
psql -h localhost -p 5432 -U admin -d ventas
```

## Persistencia de Datos

Los datos de PostgreSQL se persisten en un volumen de Docker, por lo que se mantendrán incluso si detienes o reinicias el contenedor.