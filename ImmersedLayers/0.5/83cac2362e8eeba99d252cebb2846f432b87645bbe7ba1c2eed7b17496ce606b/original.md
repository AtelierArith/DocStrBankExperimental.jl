```
x_gridgrad(::BasicILMCache)
```

Return basic grid gradient field data filled with the grid `x` coordinate. If the grid data is scalar, then the output of this function is of `Edges{Primal}` type and the coordinate field for each component can be accessed with the `u` and `v` field, respectively. If the grid data is vector, then the output is of type `EdgeGradient{Primal}`, and the coordinates are in `dudx`, `dudy`, `dvdx`, and `dvdy` fields.
