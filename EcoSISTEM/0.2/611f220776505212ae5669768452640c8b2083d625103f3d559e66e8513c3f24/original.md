```
convert_coords(eco, i::Int64, width::Int64)
convert_coords(eco, x::Int64, y::Int64, width::Int64)
```

Function to convert coordinates from two-dimensional (`x`,`y`) format to one dimension (`i`), or vice versa, using the `width` of the grid. This function can also be applied to arrays of coordinates.
