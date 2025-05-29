```
CellSpace(gridSize::NTuple{N, T}; periodic=true, diagonal=false)
CellSpace(gridSize::T...; periodic=true, diagonal=false) where T<:Integer
```

A concrete type that stores the underlying space cells will occupy.

A `CellSpace()` can be created by supplying a tuple of dimensions or multiple arguments for each dimension, e.g. `CellSpace((3,3,4))` or `CellSpace(3,3,4)`. There are two optional keyword arguments:

  * periodic `::Bool`: Determines if the grid has periodic boundaries
  * diagonal `::Bool`: Adjacent cells can have vonNeumann (default) or Moore neighborhoods. VonNeumann neighborhoods **do not** include adjacent diagonal positions.
