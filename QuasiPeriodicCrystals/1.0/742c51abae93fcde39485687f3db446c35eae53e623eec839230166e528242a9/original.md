Función que dado un Punto, obtiene aproximadamente los enteros asociados a la tesela del arreglo cuasiperiódico que lo contiene.

`Site` - son las coordenadas de un punto en el espacio 2D. `AvgDist` -  es la separación promedio entre las franjas cuasiperiódicas. `StarVecs` - son los vectores estrella del GDM.

Generemos un arreglo en donde irán los números reales resultado de proyectar el sitio con los vectores estrella. Para cada vector estrella, proyectamos el sitio sobre dicho vector y reescalamos con la separación entre las franjas cuasiperiódicas.
