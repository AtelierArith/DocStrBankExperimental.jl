```
surface(px, py, pz, option::Int)
```

Draw a three-dimensional surface plot for the given data points.

**Parameters:**

`x` :     A list containing the X coordinates `y` :     A list containing the Y coordinates `z` :     A list of length `len(x)` * `len(y)` or an appropriately dimensioned     array containing the Z coordinates `option` :     Surface display option (see table below)

`x` and `y` define a grid. `z` is a singly dimensioned array containing at least `nx` * `ny` data points. Z describes the surface height at each point on the grid. Data is ordered as shown in the following table:

```
+------------------+--+--------------------------------------------------------------+
|LINES             | 0|Use X Y polylines to denote the surface                       |
+------------------+--+--------------------------------------------------------------+
|MESH              | 1|Use a wire grid to denote the surface                         |
+------------------+--+--------------------------------------------------------------+
|FILLED_MESH       | 2|Applies an opaque grid to the surface                         |
+------------------+--+--------------------------------------------------------------+
|Z_SHADED_MESH     | 3|Applies Z-value shading to the surface                        |
+------------------+--+--------------------------------------------------------------+
|COLORED_MESH      | 4|Applies a colored grid to the surface                         |
+------------------+--+--------------------------------------------------------------+
|CELL_ARRAY        | 5|Applies a grid of individually-colored cells to the surface   |
+------------------+--+--------------------------------------------------------------+
|SHADED_MESH       | 6|Applies light source shading to the 3-D surface               |
+------------------+--+--------------------------------------------------------------+
```
