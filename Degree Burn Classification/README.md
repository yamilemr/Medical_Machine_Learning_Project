# **Clasificación de imágenes de quemaduras de segundo y tercer grado utilizando SVM y CNN**

Los siguientes notebooks son parte del proyecto final de la materia 'Machine Learning', que se imparte en la Licenciatura en Inteligencia Artificial de la Universidad Autónoma del Estado de Morelos. El proyecto consiste en aplicar métodos de clasificación a un dataset, con el objetivo de encontrar el mejor modelo que logre generalizar la clasificación para datos no vistos.

En este caso, se utilizaron fotos proporcionadas por la enfermera Maria Luisa Rodríguez, las cuales son de pacientes con quemaduras de segundo y de tercer grado, y estas se encuentran en diferentes partes del cuerpo.

Todas las fotos fueron recortadas manualmente para conservar únicamente la parte de la quemadura. Se eliminaron las fotos con mucho ruido en el fondo, de igual modo, fueron eliminadas aquellas que mostraban rostros. La base de datos final cuenta con 114 fotos de quemaduras de segundo grado y con 111 fotos de quemaduras de tercer grado.

Los métodos a emplear fueron 'Máquina de Soporte Vectorial (SVM)' con el kernel RBF y 'Red Neuronal Convolucional (CNN)' con 60 y 100 épocas. Las imágenes se procesaron de manera que se pudiera analizar el impacto de cada canal de color en el rendimiento de los modelos de clasificación. Este enfoque permitió probar modelos con cada uno de los canales de forma individual (rojo, verde, azul) y con todas las combinaciones posibles de estos canales (rojo y verde, rojo y azul, verde y azul, los tres canales combinados (RGB)).

## Comparación de las métricas de rendimiento de todos los modelos

|                     | <span style="color:#699DFB;">Train Accuracy</span> | <span style="color:#699DFB;">Test Accuracy</span> | <span style="color:#699DFB;">Test Precision</span>       | <span style="color:#699DFB;">Test Recall</span>          | <span style="color:#699DFB;">Test F1 Score</span>        |
|---------------------|----------------|---------------|-----------------|-----------------|-----------------|
| <span style="color:#F58C69;">**SVM**</span>             |                |               |                 |                 |                 |
| **Rojo**                | 0.9267         | 0.7941        | 0.7894          | 0.8333          | 0.8108          |
| **Verde**               | 0.9476         | 0.8823        | 0.8888          | 0.8888          | 0.8888          |
| **Azul**                | 0.9528         | 0.8529        | 0.8421          | 0.8888          | 0.8648          |
| **Rojo y Verde**        | <span style="color:#C3E88D;">**0.9688**</span>     | <span style="color:#C3E88D;">**0.8823**</span>    | <span style="color:#C3E88D;">**0.8888**</span>      | <span style="color:#C3E88D;">**0.8888**</span>      | <span style="color:#C3E88D;">**0.8888**</span>      |
| **Rojo y Azul**         | 0.9581         | 0.8529        | 0.8421          | 0.8888          | 0.8648          |
| **Verde y Azul**        | 0.9581         | 0.8529        | 0.8421          | 0.8888          | 0.8648          |
| **RGB**                 | 0.9633         | 0.8529        | 0.8421          | 0.8888          | 0.8648          |
| <span style="color:#F58C69;">**CNN 100 épocas**</span>             |                |               |                 |                 |                 |
| **Rojo**                | 0.9722         | 0.7555        | 0.625           | 0.8823          | 0.7317          |
| **Verde**               | 1.0            | 0.9333        | 0.9375          | 0.8823          | 0.9090          |
| **Azul**                | 1.0            | 0.8888        | 0.875           | 0.8235          | 0.8484          |
| **Rojo y Verde**        | 1.0            | 0.9111        | 0.8823          | 0.8823          | 0.8823          |
| **Rojo y Azul**         | 1.0            | 0.8           | 0.7222          | 0.7647          | 0.7428          |
| **Verde y Azul**        | 1.0            | 0.9333        | 0.8888          | 0.9411          | 0.9142          |
| **RGB**                 | 1.0            | 0.9333        | 0.9375          | 0.8823          | 0.9090          |
| <span style="color:#F58C69;">**CNN 60 épocas**</span>             |                |               |                 |                 |                 |
| **Rojo**                | 0.9444         | 0.9333        | 0.85            | 1.0             | 0.9189          |
| **Verde**               | <span style="color:#C3E88D;">**1.0**</span>        | <span style="color:#C3E88D;">**0.9555**</span>    | <span style="color:#C3E88D;">**0.8947**</span>      | <span style="color:#C3E88D;">**1.0**</span>         | <span style="color:#C3E88D;">**0.9444**</span>      |
| **Azul**                | 1.0            | 0.8444        | 0.9166          | 0.6470          | 0.7586          |
| **Rojo y Verde**        | 0.9944         | 0.9333        | 0.85            | 1.0             | 0.9189          |
| **Rojo y Azul**         | 1.0            | 0.9333        | 0.9375          | 0.8823          | 0.9090          |
| **Verde y Azul**        | 1.0            | 0.9333        | 1.0             | 0.8235          | 0.9032          |
| **RGB**                 | 0.9944         | 0.9111        | 0.8823          | 0.8823          | 0.8823          |

Con esta tabla comparativa se puede notar que el modelo de SVM con mejor rendimiento fue el que utiliza los canales rojo y verde. Sin embargo, el mejor modelo es el que utiliza Redes Neuronales Convolucionales con 60 épocas y que se queda con el canal verde de las imágenes.

## Conclusión:

A pesar de que el modelo aún comete errores, considero que es un buen clasificador de imágenes de quemaduras de segundo y tercer grado, ya que pude notar que las imágenes que clasifica mal o que clasifica bien pero con una probabilidad baja, es porque son quemaduras que pertenecen a ambas clases; es decir, son combinadas. 

Adicionalmente, si se le proporciona una imagen de una quemadura de tercer grado pero que ya va mejorando, la clasifica como de segundo grado, lo cual puede considerarse como correcto, debido a que las quemaduras de tercer grado que van cicatrizando, visualmente son iguales a las de segundo grado.

## Referencias:

1. Pérez, E., Guzmán, J., Lozano, J., Torres, M., & Guzmán, R. (2022, enero). *Clasificación de imágenes médicas mediante aprendizaje automático.* Dyna, vol. 97(1), pp.35-38. [DOI: 10.6036/10117](https://doi.org/10.6036/10117). Recuperado de: https://www.researchgate.net/profile/Rafael-Guzman-Cabrera/publication/357860723_Clasificacion_de_imagenes_medicas_mediante_aprendizaje_automatico/links/61e30ac29a753545e2d1e800/Clasificacion-de-imagenes-medicas-mediante-aprendizaje-automatico.pdf

2. Tang, H., & Hu, Z. (2020, 11 de mayo). *Research on Medical Image Classification Based on Machine Learning.* IEEEAcces, vol. 8, pp.93145-93154. Recuperado de: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9091175

3. Maruyama, T., Hayashi, N., Sato, Y., Hyuga, S., Wakayama, Y., Watanabe, H., Ogura, A., & Ogura, T. (2018, 27 de diciembre). *Comparison of medical image classification accuracy among three machine learning methods.* Journal of X-Ray Science and Technolog, vol. 26(6), pp.885-893. DOI: 10.3233/XST-18386. Recuperado de: https://content.iospress.com/articles/journal-of-x-ray-science-and-technology/xst18386