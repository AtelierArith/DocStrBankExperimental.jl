```
drawpath(points, codes, fill::Int)
```

Draw simple and compound outlines consisting of line segments and bezier curves.

**Parameters:**

`points` :     (N, 2) array of (x, y) vertices `codes` :     N-length array of path codes `fill` :     A flag indication whether resulting path is to be filled or not

The following path codes are recognized:

```
+----------+-----------------------------------------------------------+
|      STOP|end the entire path                                        |
+----------+-----------------------------------------------------------+
|    MOVETO|move to the given vertex                                   |
+----------+-----------------------------------------------------------+
|    LINETO|draw a line from the current position to the given vertex  |
+----------+-----------------------------------------------------------+
|    CURVE3|draw a quadratic Bézier curve                              |
+----------+-----------------------------------------------------------+
|    CURVE4|draw a cubic Bézier curve                                  |
+----------+-----------------------------------------------------------+
| CLOSEPOLY|draw a line segment to the start point of the current path |
+----------+-----------------------------------------------------------+
```
