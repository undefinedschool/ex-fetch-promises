# Project 3: Meme Of The Day

Este es un ejercicio para practicar hacer _requests_ usando [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch), [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises), modularización y refactoring del código.

## Parte 1: Request y procesamiento de los datos

1. Crear un repo en GitHub para el código del ejercicio. Clonarlo para trabajar de forma local.
2. Dentro del repo, crear un archivo `index.js`, donde va a estar nuestro código
3. Hacer un _request_ de tipo `GET` al endpoint `https://api.imgflip.com/get_memes`, usando `Fetch API`
4. A partir de la respuesta obtenida, generar el siguiente resultado:
  - Quedarnos sólo con las propiedades `id`, `name`, `width`, `height` y `url` (en ese orden) de cada elemento del array. Omitir el resto (**Tip:** usar _destructuring_ + _spread operator_ para esto). Ver ejemplo más abajo.
  - Generar un nuevo array de _memes_, donde cada uno tendrá las propiedades mencionadas en el ítem anterior
  - En este array, filtraremos aquellos elementos cuyas propiedades `width` y `height` tengan un valor < `500`
  - Ordenar el array por `id`, de forma ascendente
5. Mostrar el resultado en la consola. Recordá que podés usar `console.dir` para visualizar mejor objetos
6. Usar siempre nombres declarativos para las variables, constantes, etc. [Guía de buenas prácticas](https://github.com/undefinedschool/best-practices)

```js
// resultado esperado
[
 {
   id: "93895088",
   name: "Expanding Brain",
   width: 857,
   height: 1202,
   url: "https://i.imgflip.com/1jwhww.jpg"
 },
 ...
]
```

## Parte 2: Modularizar y refactorizar

Vamos a separar el código en 2 archivos, `api.js` y `index.js`. Usar [ES6 Modules](https://github.com/undefinedschool/es6-modules/) para exportar e importar entre ambos.

- `api.js` va a contener el código necesario para realizar el _request_ a la API y retornar el array de memes _original_, sin modificaciones. 
  - este código irá dentro de la función `getMemes(URL)`, que recibe la _url_ como parámetro
  - guardar el endpoint de la API en una constante global `ENDPOINT`
- `index.js` va a importar la función `getMemes()` de `api.js`, invocarla y hacer todo el procesamiento posterior que hicimos en la parte 1
  - modularizar los diferentes procesamientos que hacemos en los _callbacks_ en funciones y usarlas 

## Parte 3: Random!

1. Escribir la función `getRandomMeme()` que reciba un array de memes (resultado de la parte 2) y retorne, de forma aleatoria, algún _meme_ del mismo
  - Estudiar posibilidades de modularizar esta función

## Parte 4: Render

1. Crear un `index.html` en el mismo repo, usando la estructura predefinida de un HTML5 vacío
2. Crear dentro un `div` con la clase `container`
  - Usar Flexbox para centrar (horizontal y verticalmente) todo el contenido de este div
  - Agregarle un `h1` con el texto "Meme of the Day"
  - Agregarle **debajo** un tag `img` con la clase `meme` y ocultarla con CSS, seteando su atributo `display` (en el archivo CSS de la [parte 5]())
  - Agregar un botón **debajo** del `img`, con la clase `btn-get-meme` y el texto "Get Meme!"

Abajo se muestra cómo quedaría la estructura

```
  container
    |-- h1
    |-- img
    |-- button
```

3. Al hacer click en el botón, debe ocurrir lo siguiente:
  - Ocultar el `h1`, modificando su atributo `display``
  - Modificar el texto del botón a "Get another random meme!"
  - Utilizar la función `getRandomMeme()` de la parte 3 para obtener un meme aleatorio
    - Setear la `url` del meme como `src` de la imagen
    - Setear el `name` del meme como `alt` de la imagen
    
## Parte 5: Estilizando

Crear y linkear elarchivo `styles.css`, donde irá todo el código que usaremos para los estilos

1. Aplicar el _reset_ de `padding: 0`, `margin: 0` y `box-sizing: border-box` donde corresponda
2. Usar fuentes de Google Fonts para los `h1`y `h2`
3. Aplicar los estilos necesarios para que los elementos del container queden con la estructura y orden definidos en la [parte 4]()
4. Aplicar márgenes entre los diferentes elementos del container
5. Agregar [efectos y transiciones](https://dev.to/webdeasy/top-20-css-buttons-animations-f41) al botón, al hacerle _hover_ y clickearlo
6. Al hacer _hover_ sobre la imagen del meme, se debe visualizar un texto **arriba** de la imagen, con el `name` del meme como texto, ver [texto con transición _fade in_](https://www.w3schools.com/howto/howto_css_image_overlay.asp) como ejemplo. 
