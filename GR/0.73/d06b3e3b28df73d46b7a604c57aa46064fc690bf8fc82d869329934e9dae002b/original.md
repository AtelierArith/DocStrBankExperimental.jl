```
contourf(px, py, h, pz, major_h::Int)
```

Draw filled contours of a three-dimensional data set whose values are specified over a rectangular mesh.

**Parameters:**

`x` :     A list containing the X coordinates `y` :     A list containing the Y coordinates `h` :     A list containing the Z coordinate for the height values `z` :     A list of length `len(x)` * `len(y)` or an appropriately dimensioned     array containing the Z coordinates `major_h` :     (intended for future use)
