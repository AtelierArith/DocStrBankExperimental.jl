```
contour(px, py, h, pz, major_h::Int)
```

Draw contours of a three-dimensional data set whose values are specified over a rectangular mesh. Contour lines may optionally be labeled.

**Parameters:**

`x` :     A list containing the X coordinates `y` :     A list containing the Y coordinates `h` :     A list containing the Z coordinate for the height values `z` :     A list of length `len(x)` * `len(y)` or an appropriately dimensioned     array containing the Z coordinates `major_h` :     Directs GR to label contour lines. For example, a value of 3 would label     every third line. A value of 1 will label every line. A value of 0     produces no labels. To produce colored contour lines, add an offset     of 1000 to `major_h`.
