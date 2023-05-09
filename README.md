# Mejor de Mira
AWS Hack4Good 2023

Mejor de Mira es una aplicación móvil para Android que ayuda a las personas personas con discapacidad visual a navegar por los supermercados con la asistencia de servicios de voz.

<img src="https://github.com/thelearner411/MDM/blob/main/mas_de_mira/assets/mejor-de-mira-screen.png" alt="Mejor de Mira Screen" style="display: block; margin: auto;"/>

## Lenguaje de Programación

Mejor de Mira fue programado en el lenguaje Dart usando el SDK de Flutter.


## Los Servicios de AWS

Utilizamos varios servicios de AWS para facilitar el proceso:

- <b>Amazon Recognition</b> para entrenar productos y recibir sus etiquetas.
- <b>Amazon S3 Bucket</b> para guardar las imágenes de los productos para el entrenamiento de Rekognition y también para almacenar imágenes de los productos capturadas por el usuario.
- <b>Amazon API Gateway</b>
  - para hacer una solicitud PUT cuando el usuario captura una foto de un producto que se carga en el S3 bucket.
  - para hacer una solicitud GET y recibir la etiqueta precedida de la imagen capturada usando el modelo entrenado con Rekognition.
- <b>Amazon Polly</b>
  - para repetir en voz alta una lista predefinida por el usuario.
  - pra decir la etiqueta de un producto escaneado.


### Variables importantes:
En la pantallas de carrito, hay una variable llamada <b>${POOL_ID}</b>. Este es un ID de Amazon Cognito que usamos para acceder a AWS Polly para la conversión de texto a voz. En esta pantalla, AWS Polly dice la lista de compras predefinida.

En la pantalla de cámara, hay tres variables secretas:
- <b>${IMG_UPLOAD_API_URL}</b>: la URL de la API que permite a los usuarios escanear fotos de productos que se cargan en el S3 bucket.
- <b>${PREDICTION_API_URL}</b>: la URL de la API que accede al modelo de AWS Rekognition que responde con la etiqueta del producto.
- <b>${POOL_ID}</b>: el ID de Amazon Cognito que es un requisito para que AWS Polly diga la etiqueta. En esta pantalla, AWS Polly dice la etiqueta del producto capturado.
