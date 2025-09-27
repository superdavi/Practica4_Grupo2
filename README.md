## INTEGRANTES.
| Nombre | Cargo | URL GitHub |
|---|:---:|---:|
| Daniel Alquinga | :technologist: Desarrollador | https://github.com/superdavi/Practica4_Grupo2 |
| Daniel Baldeon | :technologist: Desarrollador | https://github.com/debpdhs/Practica4_Grupo2 |
| Bryan Miño | :technologist: Desarrollador | https://github.com/bmiomi/tarea4-grupo2.git |
| Wilson Segovia | :technologist: Desarrollador | https://github.com/segoviawilson/Practica4_Grupo2.git |
| Leonardo Tuguminago | :technologist: Desarrollador | https://github.com/Tuguminago/Practica4_Grupo2.git |

# 1. Despliegue de entorno de automatización con n8n integrados con PostgreSQL en Docker Compose

El objetivo de este trabajo es desplegar una aplicacion con n8n esta esta integrada con su propia base de datos PostgreSQL, utilizando Docker Compose. Se busca aplicar  conceptos de orquestación de contenedores, persistencia de datos, separación de servicios y buenas prácticas en la gestión de entornos

# 2. Configuración e Instalación

### PASO 1: 📂 Estructura de Archivos

<img width="272" height="262" alt="image" src="https://github.com/user-attachments/assets/135d358c-39e4-4d08-b6e3-4adc96bd15a9" />

*Salida esperada*

![01](https://github.com/user-attachments/assets/fe0848a2-df64-4edf-9662-23dd18a6f416)

### PASO 2: Creacion de la red de docker

```bash
docker network create n8n-network
```
**Salida Esperada**

<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/5039de80-5981-4c76-be0e-28ce9c89b8e7" />
<br /><br />
<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/fc9fe236-4982-4579-8445-f21e00edbef4" />

### PASO 3: Despliegue de contenedor de n8n

Nos ubicamos en la carpeta n8n y ejecutar el siguiente comando

```bash
cn n8n
docker compose -f docker-compose-n8.yml up -d
```

**Salida Esperada**

<img width="1012" height="212" alt="image" src="https://github.com/user-attachments/assets/e0d7f825-ef7d-4e26-84ae-f746241bbe64" />



<img width="1012" height="212" alt="image" src="https://github.com/user-attachments/assets/ac907470-8a62-4836-ba49-733f1ec3bc25" />

<img width="1012" height="212" alt="image" src="https://github.com/user-attachments/assets/deea351b-2de0-4778-9032-aa3405408101" />

### PASO 4: Despliege de Contenedor Postgres

Ya que nos encontramos en la carpeta n8n  es necesario ejecutar la siguiente linea de comando.

```bash
docker compose -f ../postgres/compose.postgres.yml  up -d
```

**Salida Esperada**

<img width="1134" height="256" alt="image" src="https://github.com/user-attachments/assets/7b050802-200e-443a-8481-73df2b8ff54b" />

<img width="1134" height="256" alt="image" src="https://github.com/user-attachments/assets/fda093fc-4b8b-42b3-ac2b-003cba799bb5" />

<img width="1134" height="256" alt="image" src="https://github.com/user-attachments/assets/d2a35ac3-a5af-43a9-98e4-876e92a25663" />

<img width="1134" height="256" alt="image" src="https://github.com/user-attachments/assets/d2a35ac3-a5af-43a9-98e4-876e92a25663" />

<img width="1134" height="256" alt="image" src="https://github.com/user-attachments/assets/6bb6c9e3-8400-4b08-baf3-083fc8fc94c0" />

### PASO 5: Revisamos contenedores levantados

```bash
    docker ps
```

**Salida Esperada**

<img width="1200" height="200" alt="image" src="https://github.com/user-attachments/assets/b4ccbbb6-3ea8-426b-9857-fd6b50e26024" />

### PASO 6: Ingreso al portar del Servidor N8N 

Se ingresan los datos del usuario y sus datos solicitados:

```bash
    http://localhost:5678/

    Usuario: grupo2@hotmail.com
    Nombre: grupo2
    Apellido: practica4
    Password: Mi1Pass3Seguro4!
```

**Salida Esperada**

<img width="1192" height="737" alt="image-1" src="https://github.com/user-attachments/assets/40c630bb-8653-438e-acbe-1836656943b8" />


### PASO 8: Informacion adicional del Servidor N8N


<img width="1192" height="1000" alt="image-1" src="https://github.com/user-attachments/assets/fe5bf499-30c8-4a39-9903-e874103c3fd7" />

### PASO 9: Seccion de Gestor de Base de datos en N8N

Al lado izquierdo, se encuentra el simbolo "+", al seleccionarlo, se despliega la pantalla donde debemos escoger la base de datos Postgres

**Salida Esperada**

<img width="676" height="276" alt="image-3" src="https://github.com/user-attachments/assets/b33ff62d-437e-4b21-860f-2d759c0e11b5" />

### PASO 10: Configuracion de Credenciales 

 Parametros obtenidos del archivos .env del repositorio y el nombre del contenedor como host del postgres

```bash
    Host: postgres-db
    Database: postgres
    User: n8nuser
    Password: Super_Segura123!
```
**Salida Esperada**

<img width="1372" height="733" alt="image-4" src="https://github.com/user-attachments/assets/06d3a5ca-ee16-4248-8a97-32a6640607f4" />

<img width="1372" height="733" alt="image-4" src="https://github.com/user-attachments/assets/6c3987d2-5bf6-41fe-9ccf-ea62ee83e85a" />

<img width="1372" height="733" alt="image-4" src="https://github.com/user-attachments/assets/eaa79d30-f7f8-48f9-88a4-292c866aca26" />

### PASO 11: Verificar Ingresos.
    
   Se verifica  que la conexion sea Exitosa 

**Salida Esperada**

<img width="1331" height="725" alt="image-5" src="https://github.com/user-attachments/assets/c336f016-7d62-4e6d-9ece-6653fc8792a5" />

### PASO 12:  Verifcacion de N8N con Postgres.

   Se verifica que la conexion de la base de datos este vinculada con el contenedor N8N.

**Salida Esperada**

<img width="1600" height="318" alt="image-6" src="https://github.com/user-attachments/assets/b58e3070-a1b5-4b86-84de-6ece270b9c9b" />

# 3. Conclusiones

- Se pudo configurar correctamente el despliegue de n8n.

- Se pudo configurar el despliegue en docker de la base de datos postgres.

- Se interactua entre los dos contenedores por medio de una network creada para el caso

- Se realizan pruebas de conexión entre los contenedores al configurar el n8n con la base de datos postgres y esta ser exitosa.

- Es necesario tener en cuenta los dockers activos ya que en el caso dió un error por que tenia un docker arriba con el puerto de la base postgress al que se le paró y se contnuó con el despliegue del contenedor de postgress.

- Tener en cuenta las carpetas donde se encuentran trabajando para evitar errores al momento de ejecutar comandos.

- Uso de credenciales seguras es necesario en ambientes de test y producción.

