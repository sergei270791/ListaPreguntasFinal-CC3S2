# ListaPreguntasFinal-CC3S2

## Introducción a la entrega continua

1. ¿Cuáles son las tres fases del proceso de entrega tradicional?

  Desarrollo, Quality Assurance (QA) y operaciones.

2. ¿Cuáles son las tres etapas principales de un pipeline de CD?

  Integración continua, pruebas de aceptación automatizadas y gestión de la configuración.


3. Menciona al menos tres beneficios de usar CD.

  Entrega rápida, 
  Ciclo de retroalimentación rápido, 
  Publicaciones de bajo riesgo y 
  Opciones de liberación flexibles.


4. ¿Cuáles son los tipos de pruebas que deben automatizarse como parte del pipeline de CD?

 Pruebas unitarias, Pruebas de API/servicios, Pruebas de aceptación, Prueba del sistema, Prueba de regresión, Prueba de aceptación del usuario y Prueba de humo.

5. ¿Deberíamos tener más pruebas de integración o unitarias? Explicar por qué.

La cantidad de pruebas de integración y unitarias va a depender del tipo de proyecto, pero la regla general es que se busque cubrir la mayor parte de la lógica de negocios con pruebas unitarias, y utilizar las pruebas de integración para verificar un camino de ejecución exitoso o fallido de tu programa. 


6. ¿Qué significa el término DevOps?.

DevOps es un acrónimo inglés de development (desarrollo) y operations (operaciones), que se refiere a una metodología de desarrollo de software que se centra en la comunicación, colaboración e integración entre desarrolladores de software y los profesionales de sistemas en las tecnologías de la información (IT)




## Docker

1. ¿Cuál es la principal diferencia entre la creación de contenedores (como con Docker) y la
virtualización (como con VirtualBox)?

Que con el contenedor docker no descargas todo un sistema operativo completo si no solo el kernel y lo que necesitas para que funcione correctamente tu aplicación o servicio.

2. ¿Cuáles son los beneficios de proporcionar una aplicación como una imagen de Docker? Nombra al menos dos.

Velocidad de iteración, Mayor portabilidad y Mayor eficiencia.

3. ¿Se puede ejecutar el demonio Docker de forma nativa en Windows y macOS?

Docker está basado internamente en el kernel de Linux y sus especificaciones, y es por
eso que, en el caso de macOS y Windows, utiliza máquinas virtuales (HyperKit para macOS e Hyper-V para Windows) para ejecutar el Entorno del motor Docker.


4. ¿Cuál es la diferencia entre una imagen Docker y un contenedor Docker?

Una imagen es una especie de plantilla, una captura del estado de un contenedor. Es analogo a lo que es una clase y un objeto, osea un contenedor seria una instancia de una imagen. Además recordar que la imagen es un bloque de construcción sin estado (stateless) mientras que los contenedores tienen estado (stateful), esto significa que podemos interactuar con ellos y realizar cambios en sus estados.

5. ¿Qué significa cuando se dice que las imágenes de Docker tienen capas?

Significa que puede construir una imagen encima de otra imagen. Esto mejora la portabilidad de estas imágenes y la escalabilidad.


6. ¿Cuáles son dos métodos para crear una imagen de Docker?

El comando commit de Docker y una compilación automatizada de Dockerfile.
En el primer caso se toma como base una cierta imagen y de manera interactiva por medio de comandos se le añadiendo cosas hasta que se hace un commit y se crea una nueva imagen con todas las nuevas cosas integradas, la segunda forma consiste en poner con ciertas reglas y formatos instrucciones en un archivo dockerfile para luego construir una imagen apartir de este dockerfile. 

7. ¿Qué comando se usa para crear una imagen de Docker a partir de un Dockerfile?

docker build -t <nombre-image> .   
Con este comando se construye la imagen apartir del dockerfile que esta en la carpeta actual.
8. ¿Qué comando se usa para ejecutar un contenedor de Docker desde una imagen de Docker?

El comando run.

docker run <nombre-image>


9. En la terminología de Docker,¿qué significa publicar un puerto?

Exponer su puerto a otras aplicaciones para que se pueda comunicar con ellas. 

10. ¿Qué es un volumen Docker?

Un volumen de Docker es el directorio del host de Docker montado dentro del contenedor. Permite que el contenedor escriba en el sistema de archivos del host como si estuviera escribiendo en el suyo propio.
Los volúmenes de Docker permiten la persistencia y el uso compartido de los datos de un contenedor.
Los volúmenes también separan claramente el procesamiento de los datos.


## Jenkins

1. ¿Se proporciona Jenkins en forma de imagen de Docker?

Sí, ya que la combinación de estas dos herramientas produce resultados sorprendentemente buenos: configuración automatizada y escalabilidad flexible.


2. ¿Cuál es la diferencia entre un maestro de Jenkins y un agente de Jenkins (esclavo)?

Jenkins master delegar tareas de ejecución a Jenkins agents.el maestro de Jenkins es responsable de Recibir disparadores de construcción, Enviar notificaciones, Manejar de solicitudes HTTP y Gestionar del entorno de construcción .El agente de construcción es una máquina que se encarga de todo lo que sucede después de que se haya iniciado la construcción.


3. ¿Cuál es la diferencia entre el escalado vertical y horizontal?

El escalado vertical significa que cuando la carga del maestro crece, se aplican más recursos a la máquina del maestro.

El escalado horizontal significa que cuando una organización crece, se lanzan más instancias maestras.Esto requiere una asignación inteligente de instancias a los equipos y, en casos extremos, cada equipo puede tener su propio maestro Jenkins.


4. ¿Cuáles son las dos opciones principales para la comunicación maestro-agente al iniciar un agente Jenkins?

SSH: el maestro se conecta al agente mediante el protocolo SSH estándar. Jenkins tiene un
cliente SSH incorporado, por lo que el único requisito es el servidor SSH daemon (sshd)
configurado en los agentes. Este es el método más conveniente y estable porque utiliza
mecanismos estándar de Unix.

Java web start: se inicia una aplicación Java en cada máquina agente y se establece la conexión TCP entre la aplicación del agente Jenkins y la aplicación maestra Java. Este método se usa a menudo si los agentes están dentro de la red cortafuegos y el maestro no puede iniciar la conexión.

5. ¿Cuál es la diferencia entre configurar un agente permanente y un agente Docker permanente?

La configuración es estática, por lo que se hace exactamente igual que hicimos con los agentes permanentes. La única diferencia es que necesitamos instalar Docker en cada máquina que se usará como agente. Entonces, normalmente no necesitamos etiquetas porque todos los agentes pueden ser los mismos.

6. ¿Cuándo necesitarás crear una imagen de Docker personalizada para un agente de Jenkins?

Si tu propio agente es un contenedor de Docker y tiene algunos requisitos específicos de tiempo de ejecución de construcción. Esto significa que para un proyecto con requisitos personalizados, la configuración es un poco más compleja.

7. ¿Cuándo necesitarás crear una imagen de Docker personalizada para un maestro de Jenkins?

Cuando no queremos usar agentes en absoluto y cuando se repite la misma configuración para cada uno de los equipos ahí es mejor preparar la imagen maestra compartida y dejar que los equipos la usen.


## Pipelines

1. ¿Qué es un pipeline?

Un pipeline es una secuencia de operaciones automatizadas que normalmente representa una parte del proceso de entrega y control de calidad del software, brindan Agrupación de operaciones, Visibilidad y Feedback.

2. ¿Cuál es la diferencia entre un stage y un step en el pipeline?

Un step es una sola operación que le dice a Jenkins qué hacer mientras que un stage es una separación lógica de steps que agrupa secuencias de pasos conceptualmente distintas.

3. ¿Qué es la sección post en el pipeline de Jenkins?

El Post define una serie de instrucciones de uno o más pasos que se ejecutan al final de la
construcción del pipeline; están marcados con una condición (por ejemplo, always, success o failure) y generalmente se usan para enviar notificaciones después de la construcción del
pipeline.

4. ¿Cuáles son las tres etapas más fundamentales del commit pipeline?

Checkout: Esta etapa descarga el código fuente del repositorio.

Compile: esta etapa compila el código fuente.

Unite test: esta etapa ejecuta un conjunto de pruebas unitarias.

5. ¿Qué es un Jenkinsfile?

Es una archivo donde que hace lo del script pipeline, para que vaya como parte de tu repositorio, junto con el código fuente y es aún más consistente porque la apariencia de un pipeline está estrictamente relacionada con el proyecto en sí.

6. ¿Cuál es el propósito de la etapa de cobertura de código?

Nos aseguramos de que el código sea probado, y así asegurar que el código funcione como se esperaba y verifique qué partes del código se han ejecutado. Luego, puedes crear un informe que muestre las secciones no probadas. Además, podemos hacer que la construcción falle cuando hay demasiado código sin probar.


7. ¿Cuál es la diferencia entre los siguientes triggers de Jenkins: external y polling SCM ?

En externa Jenkins inicia la construcción después de que lo llame el notificador (notifier), que puede ser otra construcción de un pipeline, mientras que en polling SCM podemos configurar un triggers automático agregando la declaración triggers (justo después del agente) al pipeline.

8. ¿Cuáles son los métodos de notificación de Jenkins más comunes? Nombra al menos tres.

Correo electrónico, Chats grupales y Espacios de equipo.

9. ¿Cuáles son los tres flujos de trabajo de desarrollo más comunes?.

Trunk-based workflow: Hay un repositorio central con una sola entrada para todos los cambios en el proyecto, que se denomina trunk o master. Cada miembro del equipo clona el repositorio central para tener sus propias copias locales. Los cambios se envían directamente al repositorio central.

Branching workflow  significa que el código se guarda en muchas ramas diferentes. Esto facilita que varios desarrolladores trabajen en una característica sin romper la base del código principal.

Forking workflow significa literalmente crear un nuevo repositorio a partir de otro repositorio. Los desarrolladores envían a sus propios repositorios, y cuando quieren integrar código, crean un pull request para el otro repositorio.

## Pruebas de aceptación automatizadas

1. ¿Qué es el Docker Registry?

Docker Registry es un almacén de imágenes de Docker. Para ser precisos, es una aplicación de servidor sin estado que permite que las imágenes se publiquen (push) y luego se recuperen (pulled).

2. ¿Qué es Docker Hub?

Docker Hub proporciona un servicio de Docker registry y otras funciones relacionadas, como crear imágenes, probarlas y extraer código directamente del repositorio de código. Docker Hub está alojado en la nube, por lo que realmente no necesita ningún proceso de instalación.

3. ¿Cuál es la convención para nombrar las imágenes de Docker

La convención es <registry_address>/<image_name>:<tag>, por ejemplo: sergei1222/calculador:caching

4. ¿Cuál es el entorno staging?

Es una etapa previa a la prueba de aceptacion donde se ejecuta como un demonio, publica su puerto y se le indica que se  elimine automáticamente cuando se detenga.

5. ¿Qué comandos de Docker usaría para crear una imagen y enviarla (push) a Docker Hub?

Para crear la imagen build y para enviarla push, pero antes tambien usaria login para enviarla a docker hub.Por ejemplo: 

docker build -t sergei1222/calculador

docker login 

docker push sergei1222/calculador

6. ¿Cuál es el objetivo principal de los frameworks de prueba de aceptación como Cucumber y FitNesse?
La empresa, entiende lo que se necesita escrito para ofrecer un valor comercial pero no cómo hacerlo; por otro lado, el equipo de desarrollo sabe cómo pero no sabe qué se necesita. Así que el objetivo principal de estos frameworks es ayudar a conectar estos dos mundos.

7. ¿Cuáles son las tres partes principales de una prueba de Cucumber?

Crear criterios de aceptación

Crear definiciones de pasos

Ejecutar una prueba de aceptación automatizada

8. ¿Qué es la aceptación TDD?

Los usuarios (con los desarrolladores) escriben la especificación de los criterios de aceptación en el formato DSL fácil de usar. Los desarrolladores escriben los accesorios y las pruebas fallan. Luego, el desarrollo de características comienza a utilizar la metodología TDD internamente. Una vez que se completa la característica, la prueba de aceptación debe pasar, y esto es una señal de que la característica se completó.

## Kubernetes

1. ¿Qué es un clúster de servidores?

Un clúster de servidores es un conjunto de computadoras conectadas que funcionan juntas de tal manera que se pueden usar de manera similar a un solo sistema. Los servidores suelen estar conectados a través de la red local mediante una conexión lo suficientemente rápida como para garantizar que los servicios que se ejecutan se distribuyan.

2. ¿Cuál es la diferencia entre un plano de control de Kubernetes y un nodo de Kubernetes?

El plano de control de Kubernetes (maestro), que en realidad es un conjunto de servicios de clúster, es responsable de hacer cumplir el estado deseado de tus aplicaciones, mientras que Un nodo de Kubernetes, por otro lado, es un trabajador. Puedes verlo simplemente como un host de contenedor (Docker) con un proceso especial de Kubernetes (llamado kubelet) instalado.

3. Menciona al menos tres plataformas en la nube que proporcionen un entorno de Kubernetes listo para usar.

GCP, Azure, AWS e IBM Cloud.

4. ¿Cuál es la diferencia entre una implementación y un servicio de Kubernetes?

El papel de la implementación es de construir y definir los pods y exponer sus puertos.

El papel de un servicio (Services) de Kubernetes es acceder a una aplicación desde el exterior.

5. ¿Cuál es el comando de Kubernetes para escalar implementaciones?

El comando para esto es kubectl scale, lo cual permite escalar hacia arriba y hacia abajo las
implementaciones, por ejemplo: 

kubectl scale --replicas 5 deployment calculador-deployment

6. Nombre al menos dos sistemas de administración de clústeres que no sean Kubernetes.

Docker Swarm, Apache Mesos, AWS Fargate, OpenShift, Rancher, Nomad y Azk.
