# OpenGL
## Librerias

### GLFW

¿Qué hace? Crea la ventana y gestiona el teclado/ratón.

- Sin ella: C++ solo puede escribir texto en una consola negra (como el típico "Hola Mundo").

- Su función real: Habla con Windows (o el sistema que uses) para pedirle un trozo de pantalla. Cuando tú pulsas la tecla R en tu código, es GLFW quien intercepta esa señal de Windows y te la pasa "masticada" para que tú la uses en el switch.

- Dato clave: Es la que mantiene el programa vivo con el bucle while(!glfwWindowShouldClose)


GLFW es una biblioteca de código abierto dedicada a la gestión de ventanas con soporte para OpenGL, OpenGL ES y Vulkan. Se trata de una biblioteca escrita en C adaptada a múltiples plataformas (MS-Windows, MacOS, X11, Wayland). Las funciones de la biblioteca dan soporte a múltiples ventanas, monitores y eventos de teclado, ratón, joystick e incluso mando de consolas.

La web oficial de la biblioteca es https://www.glfw.org/. En esta página se puede encontrar toda la documentación de la biblioteca así como la zona de descarga. Para el desarrollo de estas prácticas se ha incluido ya la distribución de GLFW en el directorio \ComputerGraphics\Tools.

Para utilizar GLFW hay que comenzar ejecutando la función glfwInit(). Al terminar la aplicación debe ejecutarse glfwTerminate() para liberar todos los recursos que pueda haberse creado. La biblioteca define la estructura GLFWwindow para describir las ventanas. Para crear una ventana se utiliza la función glfwCreateWindow() y para destruirla se usa glfwDestroyWindow(). Para que las funciones de OpenGL utilicen el contexto gráfico de la ventana se utiliza la función glfwMakeContextCurrent().

Las respuestas a los distintos eventos se configura por medio de punteros a funciones. La respuesta al evento de modificación del tamaño de la ventana se configura con la función glfwSetFramebufferSizeCallback(). La respuesta a los eventos de teclado se asigna con la función glfwSetKeyCallback(). La respuesta a los movimientos del ratón se indica por medio de la función glfwSetCursorPosCallback(). La respuesta a los botones del ratón se asigna con la función glfwSetMouseButtonCallback().

Típicamente las funciones de respuesta a eventos deben acceder a la información de la aplicación que ha creado la ventana. Para ello se utiliza la función  glfwSetWindowUserPointer() que permite almacenar una referencia a un objeto de cualquier tipo, lo que permite acceder posteriormente a este objeto por medio de la función glfwGetWindowUserPointer().

 La biblioteca GLFW permite también utilizar ventanas a pantalla completa. Para ello es necesario utilizar la función glfwSetWindowMonitor(), que debe incluir la referencia al monitor, el modo de vídeo utilizado, la posición y el tamaño de la ventana. El monitor puede obtenerse mediante la función glfwGetPrimaryMonitor(). El modo de vídeo utilizado en el monitor se obtiene con la función glfwGetVideoMode(). La posición y tamaño de una ventana se obtiene con las funciones glfwGetWindowSize() y glfwGetWindowPos(). Para usar una ventana normal se puede llamar a la función glfwSetWindowMonitor() con los parámetros de monitor y modo de vídeo a nulo, lo que asigna los valores por defecto. Para crear la ventana a pantalla completa es necesario indicar tanto el monitor como el modo de vídeo, así como el tamaño de la pantalla.

### GLEW

¿Qué hace? Activa las funciones modernas de tu tarjeta gráfica.

- El problema: Windows, por defecto, es muy antiguo y solo conoce funciones de OpenGL de hace 20 años. Tu RTX 4070 tiene funciones increíbles, pero C++ no sabe dónde están "físicamente" en el driver de Nvidia.

- Su función real: Cuando llamas a glewInit(), la librería escanea tu tarjeta de video y "desbloquea" las funciones modernas (como los Shaders). Sin GLEW, si intentas usar funciones de la Práctica 2, el programa petará porque no las encontrará.

La biblioteca GLEW desarrolla una pasarela para utilizar las funciones de OpenGL adaptandose a  la versión utilizada en tiempo de ejecución de forma transparente para el programador.

Para utilizar en nuestro código las funciones de OpenGL debemos incluir el fichero de cabecera GL\glew.h.

Para inicializar la biblioteca es necesario ejecutar el método glewInit() después de crear la ventana y el contexto gráfico sobre el que trabajarán las funciones de OpenGL.

Para distribuir las aplicaciones gráficas generadas con GLEW es necesario incluir en la distribución el fichero glew.dll que debe encontrarse en el directorio de ejecución de la aplicación.

### OpenGL

¿Qué hace? Es el conjunto de órdenes para dibujar.

- Su función real: No es un programa, es un idioma. Tú le dices glClear (limpia) o glDrawArrays (dibuja). OpenGL toma esas órdenes y las manda por el cable hacia la GPU.

- Es el estándar que permite que tu código funcione igual en la 4070 del PC y en la 5060 del portátil.


### GLM

¿Qué hace? Maneja las matemáticas de matrices y vectores.

- Por qué la necesitas: En Java tenías clases para todo. En C++, para mover el caza de combate, necesitas multiplicar matrices de 4x4. Podrías hacerlo a mano con arrays, pero sería una tortura.

- Su función real: Es una copia exacta de las matemáticas que usa la tarjeta gráfica. Si calculas algo con GLM en la CPU, sabes al 100% que la GPU lo entenderá igual.

### FreeImage

¿Qué hace? Carga fotos (JPG, PNG, BMP) para usarlas como texturas.

- Su función real: OpenGL sabe dibujar puntos y colores, pero no sabe qué es un archivo .jpg. FreeImage abre la foto, lee los colores de cada píxel y se los pasa a OpenGL para que los "pegue" sobre el modelo 3D del avión.

- En tu práctica: La usarás para que el caza no sea de un solo color, sino que tenga detalles de metal, logos o camuflaje.


## Montaje del proyecto

<img width="658" height="534" alt="image" src="https://github.com/user-attachments/assets/46ee8cec-71e0-48f6-aebb-3125a0bde52d" />
<img width="647" height="345" alt="image" src="https://github.com/user-attachments/assets/59241668-3378-40f9-a68c-2d1bfc91c8cd" />
<img width="651" height="434" alt="image" src="https://github.com/user-attachments/assets/2e566aaa-44c8-4cde-ae4f-b48059e4e604" />
<img width="657" height="500" alt="image" src="https://github.com/user-attachments/assets/d1f71bae-a241-495a-9d14-9de144d85dbe" />
<img width="656" height="671" alt="image" src="https://github.com/user-attachments/assets/0310621a-2574-4a27-b83a-50959ba3ab1c" />
<img width="658" height="389" alt="image" src="https://github.com/user-attachments/assets/5d9dd0b6-2301-4d3b-9787-78c5a957df25" />
<img width="657" height="517" alt="image" src="https://github.com/user-attachments/assets/b1ba0126-2679-4dfd-842f-002903509595" />
<img width="661" height="515" alt="image" src="https://github.com/user-attachments/assets/2a92ed04-6354-49a2-a50f-2e042d3dc79a" />
<img width="659" height="526" alt="image" src="https://github.com/user-attachments/assets/c1edd2cd-336b-4d75-ac34-128b8450f56b" />
<img width="657" height="390" alt="image" src="https://github.com/user-attachments/assets/b75c3021-0f07-435f-b1d0-3ed70446e1b1" />
<img width="660" height="393" alt="image" src="https://github.com/user-attachments/assets/b4a4010d-d8eb-4fe4-b799-b777d956c545" />
<img width="654" height="509" alt="image" src="https://github.com/user-attachments/assets/c0dddea6-aa97-4788-8282-c20dc19c89ed" />
<img width="651" height="405" alt="image" src="https://github.com/user-attachments/assets/a084c6c1-1fa6-45d9-8d91-2a7f5d3b4441" />

## Funciones 

### glfwInit();

¿Qué hace "bien bien"?

  Imagina que vas a montar un concierto. Antes de que llegue el público o el artista, tienes que encender los generadores, probar los micrófonos y avisar al personal. glfwInit() es eso: despierta a la librería GLFW.

  Su trabajo es hablar con tu sistema operativo (Windows 11 en tu caso) y decirle: "Oye, voy a necesitar crear ventanas, leer el teclado y usar la tarjeta gráfica, prepárate".

Parámetros:

  - No pide nada: void. Es una función de configuración global.

¿Qué devuelve?

  - GLFW_TRUE (1): Si todo ha ido bien y el sistema está listo.

  - GLFW_FALSE (0): Si algo ha fallado (por ejemplo, si tus drivers de la RTX 4070 estuvieran rotos o no hubiera una tarjeta gráfica compatible).

**Importante**

  El "Espejo" (glfwTerminate): En C++, todo lo que abres, lo tienes que cerrar (a diferencia de Java). Por cada glfwInit() que hagas al principio, debes tener un glfwTerminate() al final de tu main para que Windows recupere la memoria que le prestó a tu programa.


### glfwCreateWindow(int width, int height, const char* title, GLFWmonitor* monitor, GLFWwindow* share)

Es la que hace que aparezca la ventana física en tu monitor y, lo más importante, crea el Contexto de OpenGL (el canal de comunicación con tu RTX 4070).

Esta función pide 5 parámetros específicos. Vamos a verlos uno a uno como un ingeniero de la UHU:

1. width (Ancho): La resolución horizontal en píxeles (ej. 800).

2. height (Alto): La resolución vertical en píxeles (ej. 600).

3. title (Título): Una cadena de texto (string de C) que aparecerá en la barra superior de la ventana.

4. monitor (Monitor): * Si pasas NULL, la ventana se abre en modo ventana (normal).

  - Si pasas un puntero a un monitor (que obtienes con otra función), se abre en pantalla completa. Para tus prácticas, siempre será NULL.
  - Para elegir pantalla se consigue asi
```C++
int count;
GLFWmonitor** monitores = glfwGetMonitors(&count);
// 'monitores[0]' es el primero, 'monitores[1]' el segundo, etc.
```

5. share (Compartir): Sirve para compartir recursos entre dos ventanas (como texturas). Para aprender, siempre pondrás NULL.

**¿Qué devuelve?**
- Un puntero (GLFWwindow*): Es la "identificación" de tu ventana. En C++, a diferencia de Java, no tenemos un objeto Window que manejamos directamente; tenemos una dirección de memoria. Guardarás este puntero para decirle a otras funciones: "Oye, dibuja en esta ventana".

- NULL: Si falla (por ejemplo, si pides una resolución que tu gráfica no soporta).

## glfwSetWindowUserPointer(GLFWwindow* window, void* pointer);

Imagina que la ventana de GLFW es una caja negra que no sabe nada de tu código de la UHU. Tú tienes una clase llamada CGModel (donde está tu lógica del caza), pero GLFW solo entiende de "ventanas".

Esta función te permite "pegarle" una etiqueta con una dirección de memoria a la ventana. Es como si le dijeras a la ventana: "Oye, guarda este papelito con la dirección de mi objeto CGModel, porque más tarde te lo voy a pedir".

**Parámetros:**

1. window: El puntero a la ventana que creaste antes.

2. pointer: ¡Cualquier cosa! Es un void* (puntero genérico). Puede ser tu clase CGModel, una estructura de datos, o incluso un simple número.

### glfwSetFramebufferSizeCallback(window, framebuffer_size_callback);

Es un sensor de movimiento. Le dice a Windows: "Cada vez que el usuario estire la esquina de la ventana, avísame inmediatamente ejecutando esta función específica".

Sin esta función, si abres tu programa en una ventana de 800x600 y el usuario la maximiza a 1920x1080 (Full HD), OpenGL seguiría dibujando en un cuadradito de 800x600 en la esquina inferior izquierda, y el resto de la pantalla se vería negra o con basura.

**Parámetros:**

1. window: La ventana que queremos vigilar.

2. callback_func: El nombre de la función que tú has creado para reaccionar al cambio.

Dentro de la función que tú le pasas (framebuffer_size_callback), casi siempre verás esta línea mágica:
glViewport(0, 0, width, height);

glViewport: Es la función de OpenGL que ajusta el "lienzo" real.

Le dice a la RTX 4070: "Oye, el espacio de -1.0 a 1.0 (tus porcentajes) ahora tiene que ocupar estos nuevos píxeles de ancho y alto".

## glfwSetKeyCallback(window, key_callback);

Establece un interventor. Le dice a Windows: "Cada vez que el usuario pulse, mantenga o suelte una tecla en esta ventana, no hagas nada por defecto; llama a mi función key_callback y pásale todos los detalles".

A diferencia de un if (glfwGetKey(...)) que pregunta "¿está pulsada la 'A' ahora mismo?" (muestreo), el Callback es un evento: se activa justo en el momento exacto en que ocurre el cambio.

Parámetros:

1. window: La ventana que debe escuchar el teclado.

2. callback_func: El nombre de la función que tú has escrito.


Para que funcione, tu función key_callback debe tener exactamente estos parámetros (es el contrato que te exige GLFW):

**void key_callback(GLFWwindow* window, int key, int scancode, int action, int mods)**

1. key: La tecla (ej: GLFW_KEY_R, GLFW_KEY_ESCAPE).

2. scancode: Un código específico del hardware (útil si el usuario tiene un teclado raro, pero normalmente lo ignorarás).

3. action: Lo que está pasando. Hay tres estados:

- GLFW_PRESS: La acaba de pulsar.

- GLFW_RELEASE: La acaba de soltar.

- GLFW_REPEAT: La mantiene pulsada (útil para escribir texto).

4. mods: Si estaba pulsado Shift, Ctrl, Alt o Bloq Mayús al mismo tiempo.

## glfwSetCursorPosCallback(window, cursor_pos_callback);

Registra una función que se ejecuta cada vez que el ratón se mueve aunque sea un solo píxel. GLFW se queda "escuchando" al hardware y, en cuanto detecta movimiento, le envía a tu función las coordenadas exactas de dónde está el puntero en ese preciso instante.

**Parámetros:**

1. window: La ventana que rastrea el movimiento.

2. callback_func: Tu función encargada de procesar las coordenadas X e Y.

Tu función debe ser así para que GLFW la acepte:

void cursor_pos_callback(GLFWwindow* window, double xpos, double ypos)

- xpos: La posición horizontal del ratón en píxeles (empezando desde 0 en la izquierda).

- ypos: La posición vertical del ratón en píxeles (empezando desde 0 en la parte superior).

El "Choque" de coordenadas: El lío mental
Aquí es donde tienes que estar atento, porque se cruzan dos mundos distintos:

1. El Ratón (Píxeles): El xpos e ypos que te da esta función vienen en píxeles de ventana (ej: de 0 a 800). La Y crece hacia abajo.

1. OpenGL (NDC): Como vimos antes, para dibujar, la Y crece hacia arriba y va de -1.0 a 1.0.

¿Cómo se usa esto en la práctica?

Normalmente no usas la posición absoluta (donde está el ratón), sino el desplazamiento (offset):

- Calculas: posicion_actual - posicion_anterior.

- Si el resultado es positivo en X, el usuario ha movido el ratón a la derecha.

- Ese valor lo usas para rotar tu caza de combate.

## glfwSetMouseButtonCallback(window, mouse_button_callback);

Configura un interruptor de eventos para los botones del ratón. Al igual que con el teclado, le dice a la ventana: "No me importa dónde esté el ratón, lo que quiero es que me avises en el microsegundo exacto en el que el usuario haga clic o suelte cualquier botón".

Parámetros:

- window: La ventana que recibe el clic.

- callback_func: Tu función que decidirá qué hacer con ese clic.

La "Firma" de la función
Tu función de respuesta debe ser así:

void mouse_button_callback(GLFWwindow* window, int button, int action, int mods)

1. button: Qué botón se ha pulsado. Los más comunes:

- GLFW_MOUSE_BUTTON_LEFT (El principal/disparo).

- GLFW_MOUSE_BUTTON_RIGHT (Suele usarse para zoom o apuntar).

- GLFW_MOUSE_BUTTON_MIDDLE (La rueda).

2. action: Lo que está pasando:

- GLFW_PRESS: Justo cuando baja el botón.

- GLFW_RELEASE: Justo cuando sube.

3. mods: Si el usuario estaba haciendo, por ejemplo, Ctrl + Clic o Shift + Clic.

### glfwMakeContextCurrent(window);

Imagina que eres un artista con tres lienzos diferentes en el estudio. Tienes los pinceles en la mano, pero hasta que no te pones delante de uno de ellos, no puedes pintar.

Llamar a esta función es como decir: "A partir de este microsegundo, todas las órdenes de OpenGL que yo escriba (como glClear o glDrawArrays) se deben ejecutar en ESTA ventana específica".

En términos técnicos, crea el Contexto de Renderizado. Un contexto es como una "burbuja" de memoria en tu tarjeta gráfica que contiene todas las texturas, los shaders y los puntos del caza de combate que vas a usar.

**Parámetros:**

1. window: El puntero de la ventana que quieres activar. Si pasas NULL, desconectas la tarjeta gráfica de cualquier ventana (dejas de tener un contexto activo).

## glewInit();

Como vimos, Windows incluye por defecto una versión muy antigua de OpenGL (la 1.1). Si intentaras usar Shaders o técnicas modernas de Realidad Virtual directamente, el compilador te diría que esas funciones no existen.

glewInit() es un rastreador de funciones. Cuando la llamas:

1. Analiza qué tarjeta gráfica tienes (detecta tu 4070).

2. Mira qué versión de OpenGL soporta el driver de NVIDIA.

3. Busca las direcciones de memoria de todas las funciones modernas (como glCreateShader o glBindBuffer).

4. Las "conecta" para que tú puedas usarlas en tu código C++.

Parámetros:

No pide nada: void.

¿Qué devuelve?

Un código de error (GLenum). Si todo va bien, devuelve GLEW_OK.

Hay una regla de oro en esta asignatura que, si la rompes, tu programa se cerrará nada más abrirse:

No puedes inicializar GLEW si no hay un contexto de OpenGL activo.


## glfwSwapBuffers(window)

Esa línea es el "corazón" del renderizado en aplicaciones que usan OpenGL con la librería GLFW. Su función principal es evitar el parpadeo de la imagen mediante una técnica llamada Double Buffering (Doble Buffer).

Aquí tienes el desglose de lo que ocurre realmente cuando ejecutas esa función:

🖥️ El Concepto de Double Buffering
Sin esta técnica, el usuario vería cómo el ordenador borra la pantalla y dibuja cada triángulo uno a uno, lo que causaría un parpadeo molesto (flickering). Para evitarlo, se usan dos "lienzos" de memoria:

Front Buffer (Buffer frontal): Es la imagen que se está mostrando actualmente en el monitor.

Back Buffer (Buffer trasero): Es donde OpenGL está dibujando la nueva escena mientras tú ves la anterior.

🔄 ¿Qué hace exactamente la función?
Cuando llamas a glfwSwapBuffers(window), le dices a la tarjeta gráfica: "He terminado de dibujar en el buffer trasero; ahora intercámbialos".

- El Back Buffer pasa a ser el Front Buffer (se muestra en pantalla).

- El Front Buffer pasa a ser el Back Buffer (donde empezarás a dibujar el siguiente fotograma).

📍 Ubicación en el bucle principal
Normalmente se coloca al final de tu bucle de renderizado, justo después de todas las llamadas de dibujo y antes de procesar los eventos de entrada.

```C++
while (!glfwWindowShouldClose(window)) {
    // 1. Limpiar la pantalla
    glClear(GL_COLOR_BUFFER_BIT);

    // 2. Dibujar tus objetos (Triángulos, modelos, etc.)
    // glDrawArrays(...);

    // 3. INTERCAMBIAR BUFFERS (Mostrar lo dibujado)
    glfwSwapBuffers(window);

    // 4. Procesar eventos (teclado, ratón)
    glfwPollEvents();
}
```

#### Un toque de "Erudito": V-Sync
Si notas que la imagen se "corta" horizontalmente (un efecto llamado Tearing), es porque la tarjeta gráfica intercambia los buffers más rápido de lo que el monitor puede refrescarse.

Puedes controlar esto con:

```C++
glfwSwapInterval(1); // Activa la sincronización vertical (V-Sync)
```
Esto obliga a glfwSwapBuffers a esperar a que el monitor termine su ciclo de refresco antes de hacer el intercambio.


## glfwDestroyWindow(window)

Esta función es la encargada de hacer la "limpieza" final. Mientras que `glfwSwapBuffers` se encarga de mostrar el trabajo en cada fotograma, **`glfwDestroyWindow(window)`** se ejecuta normalmente cuando el programa ha terminado y queremos devolverle al sistema operativo todos los recursos que hemos estado usando.

Aquí tienes los detalles de lo que ocurre "bajo el capó":

### 🧹 ¿Qué hace realmente?

1. **Libera la Memoria:** Destruye el objeto de la ventana y libera la memoria RAM y de video asociada a ella.
2. **Cierra el Contexto de OpenGL:** Al destruir la ventana, también se pierde el contexto de renderizado (el "lienzo" donde OpenGL dibuja).
3. **Invalida el Handle:** El puntero `window` que has estado usando deja de ser válido. Si intentas usarlo después de esta llamada, el programa se romperá (Crash).

### 📍 ¿Dónde se coloca?

Se pone **fuera** del bucle principal (`while`), justo antes de terminar el programa o de llamar a `glfwTerminate()`.

```cpp
// --- BUCLE PRINCIPAL ---
while (!glfwWindowShouldClose(window)) {
    // Renderizado y eventos...
}

// --- LIMPIEZA ---
glfwDestroyWindow(window); // Cerramos la ventana actual
glfwTerminate();           // Cerramos GLFW por completo
return 0;

```

---

### ⚠️ Diferencia importante: `glfwDestroyWindow` vs `glfwTerminate`

Es común confundirlas, pero tienen propósitos distintos:

* **`glfwDestroyWindow(window)`**: Cierra **una ventana específica**. Si tu programa tiene tres ventanas abiertas, podrías cerrar solo una y las otras seguirían funcionando.
* **`glfwTerminate()`**: Cierra **todo**. Libera cualquier recurso que GLFW haya reservado, cierra todas las ventanas restantes y finaliza la librería. Es el "apagado general".

---

### 💡 El consejo del Erudito

Si estás desarrollando un motor de juego o una aplicación profesional, no olvides que `glfwDestroyWindow` también emite eventos. Si tienes "callbacks" registrados (funciones que se ejecutan al cerrar la ventana), este es el momento en que se terminan de gestionar.

**Dato curioso:** En la mayoría de los sistemas modernos, si te olvidas de poner esta línea, el sistema operativo liberará la memoria al cerrar el proceso de todos modos, pero es una **pésima práctica**. En aplicaciones de larga duración o herramientas que abren y cierran muchas ventanas, no usarla causaría una "fuga de memoria" (*memory leak*) que acabaría por ralentizar todo el PC.

¿Estás terminando de pulir el flujo de tu aplicación en C++ o te está dando algún error de memoria al cerrar?

### glClearColor(1.0f, 1.0f, 1.0f, 1.0f)

Esta función es, básicamente, la que elige **el color del bote de pintura** que vas a usar para "blanquear" o limpiar tu lienzo antes de empezar a dibujar un nuevo fotograma.

Como bien has puesto, `glClearColor(1.0f, 1.0f, 1.0f, 1.0f);` pone el color blanco. Pero hay un detalle técnico que separa a los programadores de Java de los de C++/OpenGL, y es entender que esta función **no pinta nada**, solo **configura**.

---

### 1. ¿Cómo funciona realmente? (Estado vs. Acción)

OpenGL es una **Máquina de Estados**. Imagina que tienes un operario en tu tarjeta gráfica:

* **`glClearColor`**: Es cuando le dices al operario: *"Oye, a partir de ahora, cada vez que te pida limpiar la pared, usa este bote de pintura blanca"*. El operario se guarda el bote, pero no hace nada todavía.
* **`glClear`**: Es cuando le das la orden: *"¡Limpia ya!"*. El operario coge el bote que le diste antes y pinta toda la pantalla.

### 2. Los parámetros (RGBA)

La función recibe cuatro valores tipo `float` que deben ir de **0.0** a **1.0**:

1. **R (Red):** Cantidad de rojo.
2. **G (Green):** Cantidad de verde.
3. **B (Blue):** Cantidad de azul.
4. **A (Alpha):** Opacidad (aunque en el fondo de la ventana no se suele notar, se pone 1.0 para que sea opaco).

> **Dato de examen:** Si pones `(1.0, 0.0, 0.0, 1.0)`, el fondo será rojo puro. Si pones `(0.0, 0.0, 0.0, 1.0)`, será negro.

### 3. ¿Dónde se coloca en el código?

Para que tu programa sea eficiente (recuerda que tu **RTX 4070** quiere ir a toda pastilla), no debes usar estas funciones a lo loco:

* **Fuera del bucle `while**`: Si el color de fondo no va a cambiar nunca, pon el `glClearColor` una sola vez al configurar OpenGL. Así el operario ya sabe qué bote usar para siempre.
* **Dentro del bucle `while**`: El `glClear(GL_COLOR_BUFFER_BIT)` tiene que ir **obligatoriamente** al principio de cada iteración del bucle. Si no limpias, el caza de combate dejará un rastro de "píxeles viejos" por toda la pantalla.

---

### Un ejemplo pro para tu práctica

Si quieres que tu simulador de vuelo parezca que tiene un cielo real, usa este color azul cielo suave:
`glClearColor(0.53f, 0.81f, 0.92f, 1.0f);`

### ¿Por qué se llama `GL_COLOR_BUFFER_BIT`?

Porque en la GPU no solo hay colores. También hay un "Buffer de Profundidad" (para saber qué objeto está delante de otro). En la Práctica 2, cuando tu caza tenga volumen, tendrás que limpiar ambos así:
`glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);`


## glViewport(0,0,w,h);

Ya que estamos diseccionando el código de tu práctica para que vayas a esa entrevista con una seguridad de hierro, vamos a profundizar en **`glViewport`**.

Como bien intuyes, esta función es el **mapeo final**: es la que transforma las coordenadas matemáticas de tu caza de combate en píxeles reales de tu monitor.

---

### ¿Cómo funciona la "Magia" del Viewport?

En el mundo de OpenGL, tú no trabajas con píxeles (tipo "pinta en el píxel 400"). Tú trabajas con **Coordenadas Normalizadas (NDC)**, que siempre van de **$-1.0$ a $1.0$** en todos los ejes.

* **Sin `glViewport`:** La GPU sabe dónde está tu triángulo en el espacio matemático, pero no sabe si tu ventana mide $800 \times 600$ o es una pantalla $4K$.
* **Con `glViewport(x, y, w, h)`:** Le das la regla de tres definitiva. Le dices: *"Oye, el $-1.0$ de mi mundo matemático equivale al píxel $0$, y el $1.0$ equivale al píxel $w$ de mi ventana"*.

---

### Los 4 parámetros explicados para un Ingeniero:

1. **`x` e `y**`: La esquina inferior izquierda. Casi siempre es `0, 0`.
2. **`w` (Width)**: El ancho en píxeles.
3. **`h` (Height)**: El alto en píxeles.

> **Dato Clave:** Si tu ventana es de $1200 \times 800$ pero tú haces `glViewport(0, 0, 600, 400);`, ¡solo verás tu dibujo en una esquinita de la ventana! El resto se quedará vacío o con el color del `glClearColor`.

---

### ¿Por qué esto es vital en las prácticas de la UHU?

El problema viene cuando el usuario **estira la ventana** con el ratón. Si no llamas a esta función de nuevo, el dibujo se verá pequeño o deformado. Por eso usamos el **Callback**:

```cpp
void framebuffer_size_callback(GLFWwindow* window, int width, int height) {
    // Esto se ejecuta CADA VEZ que el usuario cambia el tamaño de la ventana
    glViewport(0, 0, width, height);
}

```

### ¿Qué decir en la entrevista si te preguntan por esto?

Si quieres sonar como un experto en **Computación Gráfica**, di esto:

> *"Utilizo `glViewport` para definir la transformación de la ventana (Window-to-Viewport transformation). Esto asegura que las coordenadas normalizadas del pipeline de OpenGL se mapeen correctamente a las dimensiones reales del framebuffer, manteniendo la escala y evitando distorsiones cuando el usuario redimensiona la aplicación."*

---

### Un detalle curioso para tu Portátil (La 5060)

Si usas una pantalla de **alta densidad (Retina o 4K)**, a veces el ancho de la ventana en "puntos" no es el mismo que en "píxeles reales". Por eso, en lugar de usar variables manuales, solemos llamar a:
`glfwGetFramebufferSize(window, &width, &height);`
Y pasarle esos valores a `glViewport`. Así te aseguras de que el caza se vea nítido hasta en la pantalla más moderna.

**¿Te ha quedado claro el concepto del "mapeo" a píxeles?** Si es así, **¿quieres que veamos `glfwWindowHint`?** Es la función que usas **antes** de crear la ventana para decirle a Windows: *"Oye, prepárame una versión moderna de OpenGL (3.3 o superior), no me des la de hace 20 años"*. Es fundamental para que los Shaders funcionen.


## glClear(GL_COLOR_BUFFER_BIT);
Esta es la orden de ejecución. Si `glClearColor` era elegir el color del bote de pintura, **`glClear`** es el momento en el que el pintor lanza el cubo de pintura sobre el lienzo para dejarlo impecable.

Como vienes de Java, piensa en esto como el comando que "borra" lo que dibujaste en el fotograma anterior para que no se mezcle con el nuevo.

---

### 1. ¿Por qué es necesaria?

Las tarjetas gráficas (como tu **RTX 4070**) funcionan por acumulación. Si no llamas a `glClear`, OpenGL simplemente dibujará los nuevos vértices de tu caza **encima** de los del fotograma anterior.

> **El efecto "Solitario":** Sin esta función, si mueves un objeto, verás una estela infinita de ese objeto por toda la pantalla. `glClear` limpia ese rastro 60 veces por segundo.

---

### 2. El parámetro: ¿Qué estamos limpiando?

A diferencia de Java, donde sueles limpiar solo "el color", en OpenGL la GPU maneja varios tipos de memoria (buffers). Por eso no le pasamos un color, sino una **máscara de bits** (un flag):

* **`GL_COLOR_BUFFER_BIT`**: Limpia los colores de los píxeles usando el color que definiste en `glClearColor`.
* **`GL_DEPTH_BUFFER_BIT`**: (Lo verás en la Práctica 2/3) Limpia el "buffer de profundidad". Es el que sabe qué objeto está delante de otro. Si no lo limpias, el caza de combate se verá transparente o con piezas mal colocadas.
* **`GL_STENCIL_BUFFER_BIT`**: Se usa para efectos avanzados como espejos o sombras.

---

### 3. La sintaxis del "Operador Or" (`|`)

En C++, para ser ultra rápidos, limpiamos todo a la vez usando el operador `|` (OR a nivel de bits). Esto le dice a la GPU: *"Limpia el color Y la profundidad en un solo ciclo de reloj"*.

```cpp
// Lo más común en un bucle de renderizado profesional:
glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

```

---

### 4. ¿Dónde se pone?

Siempre, **siempre**, tiene que ser la **primera línea dentro de tu bucle `while**` de renderizado.

```cpp
while (!glfwWindowShouldClose(window)) {
    // 1. LIMPIAR (Preparar el lienzo)
    glClear(GL_COLOR_BUFFER_BIT);

    // 2. DIBUJAR (Pintar el caza)
    renderCaza();

    // 3. MOSTRAR (Intercambiar buffers)
    glfwSwapBuffers(window);
    glfwPollEvents();
}

```

### Para tu entrevista de prácticas:

Si te preguntan por la eficiencia, puedes mencionar que `glClear` es una de las operaciones más optimizadas por el hardware. La GPU no va píxel por píxel pintando; tiene circuitos especiales para resetear bloques enteros de memoria de video al instante.

**¿Ves la diferencia entre "configurar el color" y "ejecutar la limpieza"?** **¿Quieres que pasemos a `glfwSwapBuffers`?** Es la función "mágica" que hace que el usuario vea el resultado final sin parpadeos. Es el complemento perfecto a la limpieza.


## glfwPollEvents();
Exacto, ahora que tenemos el bucle de renderizado funcionando a toda pastilla (con el baile de punteros `0x001` y `0x002`), hay un problema: tu programa está tan concentrado dibujando que **se vuelve sordo**.

Si no incluyes **`glfwPollEvents()`**, el sistema operativo (Windows/Linux) enviará mensajes a tu ventana ("¡Eh, que han pulsado la tecla W!", "¡Que el usuario quiere cerrar la ventana!") y tu programa los ignorará. A los 5 segundos, Windows dirá: *"Este programa no responde"* y te saldrá el cursor de carga infinito.

---

### 1. ¿Qué hace realmente esta función?

Piensa en `glfwPollEvents()` como el **cartero** de tu aplicación.

Tu programa tiene una "bandeja de entrada" (una cola de eventos) donde el sistema operativo va dejando sobres. Cada sobre dice algo: "Ratón movido a X,Y", "Tecla Esc pulsada", "Ventana redimensionada".

* **Sin la función:** Los sobres se acumulan hasta que la bandeja explota y el programa se cuelga.
* **Con la función:** En cada vuelta del bucle `while`, el cartero abre todos los sobres que han llegado en ese milisegundo y ejecuta las funciones de respuesta (**callbacks**) que tú hayas configurado.

---

### 2. ¿Dónde se coloca?

Para un ingeniero de computación, el orden lógico es vital para no perder latencia (input lag):

```cpp
while (!glfwWindowShouldClose(window)) {
    // 1. Mirar si ha pasado algo (Input)
    glfwPollEvents(); 

    // 2. Limpiar y Dibujar (Process & Render)
    glClear(GL_COLOR_BUFFER_BIT);
    dibujarCaza();

    // 3. Mostrar el resultado (Output)
    glfwSwapBuffers(window);
}

```

### 3. El concepto de "Callback" (Fundamental en C++)

Aquí es donde entra la potencia de lo que sabes:
Tú no haces un `if (tecla_pulsada)` dentro de `glfwPollEvents`. Lo que haces es **registrar una función**. Le dices a GLFW: *"Si llega un sobre de teclado, llama a esta función mía que se llama `procesarTeclado`"*.

`glfwPollEvents()` es la que se encarga de buscar en la memoria esa función y ejecutarla. Es **programación dirigida por eventos**.

---

### 4. Diferencia clave: `PollEvents` vs `WaitEvents`

En tu perfil de Ícaro hablabas de **eficiencia**, y aquí hay un detalle técnico:

* **`glfwPollEvents()`**: Mira la bandeja de entrada y, si está vacía, sigue adelante inmediatamente. Es la que se usa en **juegos y simuladores** porque queremos que el caza se siga dibujando aunque no pulsemos nada.
* **`glfwWaitEvents()`**: Se queda dormido hasta que llega un sobre. Ahorra muchísima batería y CPU, pero el programa se "congela" hasta que mueves el ratón. Se usa en aplicaciones de escritorio (tipo Photoshop o un editor de texto).

---

### Tu ventaja en la entrevista de la UHU

Si el profesor o el entrevistador te pregunta por qué el programa se queda "congelado" al intentar mover la ventana, ya tienes la respuesta técnica:

> *"Es debido a que el hilo principal está bloqueado en el bucle de renderizado y no está realizando el **polling de eventos**. Al no llamar a `glfwPollEvents`, la cola de mensajes del sistema operativo se satura y la ventana deja de responder a las interrupciones del usuario."*

**¿Te ha quedado claro cómo el "cartero" evita que el SO mate tu proceso?** **¿Quieres que veamos ahora la función `glfwWindowShouldClose`?** Es la que decide cuándo ese bucle infinito tiene que parar (por ejemplo, cuando el cartero lee un sobre que dice "el usuario ha pulsado la X de la ventana"). Es la pieza final del puzzle del bucle principal.


## glfwGetTime();

Esta función es el **reloj de alta precisión** de tu aplicación. Si `glfwPollEvents` era el cartero y los buffers eran los lienzos, `glfwGetTime` es el cronómetro que te permite que tu caza de combate no se mueva a velocidades locas dependiendo de si el ordenador es un pepino o una tostadora.

---

### 1. ¿Qué devuelve exactamente?

Devuelve un valor de tipo **`double`** (doble precisión) que representa el número de segundos transcurridos desde que se inició la librería GLFW (o desde que llamaste a `glfwInit`).

> **Importante:** Al ser un `double`, tiene una precisión de microsegundos. Esto es vital porque en un juego a 60 FPS, cada fotograma dura apenas **0.01667 segundos**. Un `int` no nos serviría de nada.

### 2. El problema del "Hardware Diferente"

Si tú programas el movimiento del caza así:
`posicion.x += 0.1f; // En cada iteración del bucle`

* En un PC lento (30 FPS), el caza se moverá 3 metros por segundo ($30 \times 0.1$).
* En tu **RTX 4070** (si fuera a 300 FPS), ¡el caza se movería a 30 metros por segundo!

**Solución:** Usar el tiempo para calcular el **DeltaTime**.

---

### 3. Cómo se usa para animaciones (El truco del "Glow")

Una forma muy chula de usar esta función es para que algo cambie con el tiempo de forma suave (como una luz que parpadea o el color del caza). Puedes usar la función `sin()` (seno) con el tiempo:

```cpp
double tiempo = glfwGetTime();
float verde = static_cast<float>(sin(tiempo) / 2.0 + 0.5); // Oscila entre 0 y 1

// Luego pasas este valor al Fragment Shader para que el color cambie solo

```

### 4. La utilidad real: El DeltaTime

Para que el movimiento sea **independiente de los frames**, calculamos cuánto tiempo ha pasado exactamente desde el último fotograma:

```cpp
double tiempoActual = glfwGetTime();
double deltaTime = tiempoActual - tiempoAnterior;
tiempoAnterior = tiempoActual;

// Ahora el movimiento es constante:
posicion.x += velocidad * deltaTime; 

```

---

### Tu defensa en la entrevista técnica

Si te preguntan cómo aseguras que tu simulación sea realista, puedes soltar esta frase de "Senior":

> *"Utilizo `glfwGetTime` para implementar una lógica de **Frame Independent Movement**. Al calcular el **DeltaTime** entre iteraciones del bucle principal, aseguro que las transformaciones físicas y las animaciones se procesen de forma consistente, independientemente de la tasa de refresco (FPS) del hardware del usuario."*

Esto demuestra que no solo sabes "dibujar", sino que entiendes la **física de la computación**.

---

### ¿Lo tienes?

Es una función sencilla pero es el "corazón" que late en tu programa.

**¿Quieres que veamos ahora `glfwWindowShouldClose`?** Es la función que mira el reloj y los eventos para decidir cuándo el usuario ha dicho "basta" y hay que cerrar el chiringuito de forma limpia (liberando la memoria de los buffers que tanto nos ha costado entender).





















