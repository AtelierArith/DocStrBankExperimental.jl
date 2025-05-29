```
y_grid(::BasicILMCache)
```

Return basic grid data filled with the grid `y` coordinate. If the grid data is scalar, then the output of this function is of the same type. If the grid data is vector, then the output is of type `Edges{Primal}`, and the coordinates of each component are in `u`, `v` fields.
