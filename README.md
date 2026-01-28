# MyDockerComposes

Repositorio centralizado de configuraciones de **Docker Compose** para múltiples servicios y aplicaciones. Este proyecto facilita la orquestación y gestión de contenedores mediante archivos de composición estandarizados.

**Autor:** roaco

---

## 📋 Descripción General

Docker Compose es una herramienta que permite definir y ejecutar aplicaciones multi-contenedor mediante archivos YAML. Cada carpeta en este repositorio contiene la configuración necesaria para desplegar diferentes servicios de forma consistente y reproducible.

### Servicios Disponibles

- **GLPI** - Sistema de gestión de activos de TI y soporte técnico
- **Keycloak** - Servidor de identidad y gestión de acceso (IAM)
- **MongoDB** - Base de datos NoSQL orientada a documentos
- **MySQL** - Sistema de gestión de bases de datos relacional
- **n8n** - Plataforma de automatización de flujos de trabajo
- **PostgreSQL** - Sistema de gestión de bases de datos relacional avanzado
- **SonarQube** - Plataforma de análisis estático de código

---

## 🚀 Requisitos Previos

Antes de utilizar este repositorio, asegúrate de tener instalados:

- **Docker** (versión 20.10 o superior)
- **Docker Compose** (versión 2.0 o superior)
- **Git** (para clonar el repositorio)

### Verificar Instalación

```bash
# Verificar versión de Docker
docker --version

# Verificar versión de Docker Compose
docker compose version

# Verificar permisos de usuario (Linux/Mac)
docker ps
```

---

## 📁 Estructura del Proyecto

```
MyDockerComposes/
├── GLPI/
│   └── docker-compose.yml
├── keycloak/
│   └── docker-compose.yml
├── MongoDB/
│   └── docker-compose.yml
├── MySQL/
│   └── stack.yml
├── n8n/
│   └── docker-compose.yml
├── PostGres/
│   └── docker-compose.yml
├── SonarQ/
│   └── docker-compose.yml
└── README.md
```

---

## 📖 Guía de Uso de Docker Compose

### Comandos Principales

#### 1. **`docker compose up`**
Crea e inicia todos los contenedores definidos en el archivo `docker-compose.yml`.

```bash
# Inicia los servicios en modo interactivo
docker-compose up

# Inicia los servicios en background (modo detached)
docker-compose up -d

# Inicia y construye imágenes si es necesario
docker-compose up --build

# Inicia servicios específicos
docker-compose up servicio1 servicio2

# Inicia con output en tiempo real
docker-compose up -v
```

#### 2. **`docker compose down`**
Detiene y elimina todos los contenedores, redes y volúmenes asociados.

```bash
# Detiene y elimina contenedores
docker-compose down

# Detiene, elimina y limpia volúmenes
docker-compose down -v

# Elimina también las imágenes
docker-compose down --rmi all

# Elimina solo imágenes locales (no las descargadas)
docker-compose down --rmi local
```

#### 3. **`docker compose ps`**
Muestra el estado de todos los contenedores del proyecto.

```bash
# Lista contenedores en ejecución
docker-compose ps

# Muestra todos los contenedores (incluyendo detenidos)
docker-compose ps -a

# Salida en formato JSON
docker-compose ps --format json
```

#### 4. **`docker compose logs`**
Visualiza los registros (logs) de los contenedores.

```bash
# Muestra logs de todos los servicios
docker-compose logs

# Muestra logs de un servicio específico
docker-compose logs nombre_servicio

# Muestra últimas 50 líneas
docker-compose logs --tail 50

# Sigue los logs en tiempo real
docker-compose logs -f

# Muestra logs con timestamp
docker-compose logs --timestamps

# Combina opciones: últimas líneas en tiempo real
docker-compose logs -f --tail 100
```

#### 5. **`docker compose exec`**
Ejecuta comandos dentro de un contenedor en ejecución.

```bash
# Ejecuta un comando en un contenedor
docker-compose exec nombre_servicio comando

# Ejecuta shell interactivo
docker-compose exec -it nombre_servicio /bin/bash

# Ejecuta como usuario específico
docker-compose exec -u usuario nombre_servicio comando

# Desactiva asignación de pseudo-terminal
docker-compose exec -T nombre_servicio comando
```

#### 6. **`docker compose build`**
Construye imágenes para los servicios definidos en el archivo de composición.

```bash
# Construye todas las imágenes
docker-compose build

# Construye un servicio específico
docker-compose build nombre_servicio

# Construye sin usar caché
docker-compose build --no-cache

# Construye y etiqueta imágenes
docker-compose build --tag nombre:version
```

#### 7. **`docker compose restart`**
Reinicia los contenedores en ejecución.

```bash
# Reinicia todos los servicios
docker-compose restart

# Reinicia un servicio específico
docker-compose restart nombre_servicio

# Reinicia con tiempo de espera personalizado
docker-compose restart -t 30
```

#### 8. **`docker compose stop`**
Detiene los contenedores sin eliminarlos.

```bash
# Detiene todos los servicios
docker-compose stop

# Detiene un servicio específico
docker-compose stop nombre_servicio

# Detiene con timeout
docker-compose stop -t 30 nombre_servicio
```

#### 9. **`docker compose start`**
Inicia contenedores previamente detenidos.

```bash
# Inicia todos los servicios
docker-compose start

# Inicia servicios específicos
docker-compose start servicio1 servicio2
```

#### 10. **`docker compose pull`**
Descarga las imágenes más recientes de los registros.

```bash
# Descarga todas las imágenes
docker-compose pull

# Descarga una imagen específica
docker-compose pull nombre_servicio

# No solicita confirmación
docker-compose pull -q
```

#### 11. **`docker compose push`**
Sube imágenes a registros remotos.

```bash
# Sube todas las imágenes
docker-compose push

# Sube un servicio específico
docker-compose push nombre_servicio
```

#### 12. **`docker compose rm`**
Elimina contenedores detenidos.

```bash
# Elimina contenedores detenidos
docker-compose rm

# Elimina sin pedir confirmación
docker-compose rm -f

# Elimina volúmenes asociados
docker-compose rm -v
```

#### 13. **`docker compose config`**
Valida y muestra la configuración del archivo docker-compose.

```bash
# Muestra configuración procesada
docker-compose config

# Valida sin mostrar salida
docker-compose config -q

# Salida en formato JSON
docker-compose config --format json
```

#### 14. **`docker compose validate`**
Valida la sintaxis del archivo de composición.

```bash
# Valida el archivo docker-compose.yml
docker-compose validate

# Valida archivo específico
docker-compose -f archivo.yml validate
```

#### 15. **`docker compose events`**
Muestra eventos en tiempo real de los contenedores.

```bash
# Muestra eventos en tiempo real
docker-compose events

# Eventos de un servicio específico
docker-compose events nombre_servicio
```

---

## 🔧 Opciones Globales

Las siguientes opciones pueden usarse con cualquier comando de Docker Compose:

```bash
# Especifica archivo de composición alternativo
docker-compose -f archivo.yml up

# Especifica nombre del proyecto
docker-compose -p nombre_proyecto up

# Especifica múltiples archivos
docker-compose -f archivo1.yml -f archivo2.yml up

# Habilita soporte para perfiles
docker-compose --profile nombre_perfil up

# Verbose mode (salida detallada)
docker-compose --verbose up
```

---

## 💡 Flujos de Trabajo Comunes

### Iniciar un Servicio Completo

```bash
cd GLPI/
docker-compose up -d
docker-compose logs -f
```

### Desarrollar y Probar

```bash
# Construir imagen con cambios recientes
docker-compose up -d --build

# Acceder al contenedor
docker-compose exec -it nombre_servicio /bin/bash

# Ver logs
docker-compose logs -f nombre_servicio
```

### Actualizar Servicios

```bash
# Descargar imágenes más recientes
docker-compose pull

# Reiniciar con nuevas imágenes
docker-compose up -d

# Verificar estado
docker-compose ps
```

### Limpiar Recursos

```bash
# Detener contenedores
docker-compose stop

# Eliminar contenedores detenidos
docker-compose rm

# Eliminar volúmenes (CUIDADO: se pierden datos)
docker-compose down -v
```

### Diagnosticar Problemas

```bash
# Ver logs detallados
docker-compose logs nombre_servicio -f --tail 200

# Inspeccionar configuración
docker-compose config

# Ver eventos en tiempo real
docker-compose events

# Acceder a shell del contenedor
docker-compose exec -it nombre_servicio /bin/bash
```

---

## 🔐 Prácticas de Seguridad

1. **Variables de Entorno**: Usa archivos `.env` para credenciales (no commites credenciales)
2. **Control de Acceso**: Limita permisos de usuarios a contenedores específicos
3. **Actualizar Imágenes**: Mantén las imágenes base actualizadas regularmente
4. **Redes Aisladas**: Configura redes personalizadas para aislamiento
5. **Volúmenes**: Utiliza volúmenes nombrados en lugar de bind mounts para datos sensibles

---

## 📚 Recursos Adicionales

- [Documentación Oficial de Docker Compose](https://docs.docker.com/compose/)
- [Referencia Completa de docker-compose.yml](https://docs.docker.com/compose/compose-file/)
- [Best Practices para Docker Compose](https://docs.docker.com/compose/compose-file/best-practices/)
- [Docker Hub](https://hub.docker.com/) - Repositorio de imágenes

---

## 🤝 Contribuciones

Para contribuir al proyecto, por favor:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/mi-feature`)
3. Commit tus cambios (`git commit -m 'Agregar mi-feature'`)
4. Push a la rama (`git push origin feature/mi-feature`)
5. Abre un Pull Request

---

## 📝 Notas Importantes

- **Datos Persistentes**: Asegúrate de configurar volúmenes adecuados para bases de datos
- **Puertos**: Verifica que los puertos no estén en uso antes de iniciar servicios
- **Recursos**: Configura límites de CPU y memoria según tus necesidades
- **Redes**: Los servicios se comunican por el nombre del servicio definido en docker-compose

---

## 📄 Licencia

Este proyecto está disponible bajo licencia MIT.

---

**Última Actualización:** 27 de enero de 2026  
**Mantenedor:** roaco
