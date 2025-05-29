```
drawimage(xmin::Real, xmax::Real, ymin::Real, ymax::Real, width::Int, height::Int, data, model::Int = 0)
```

Draw an image into a given rectangular area.

**Parameters:**

`xmin`, `ymin` :     First corner point of the rectangle `xmax`, `ymax` :     Second corner point of the rectangle `width`, `height` :     The width and the height of the image `data` :     An array of color values dimensioned `width` by `height` `model` :     Color model (default=0)

The available color models are:

```
+-----------------------+---+-----------+
|MODEL_RGB              |  0|   AABBGGRR|
+-----------------------+---+-----------+
|MODEL_HSV              |  1|   AAVVSSHH|
+-----------------------+---+-----------+
```

The points (`xminx`, `ymin`) and (`xmax`, `ymax`) are world coordinates defining diagonally opposite corner points of a rectangle. This rectangle is divided into `width` by `height` cells. The two-dimensional array `data` specifies colors for each cell.
