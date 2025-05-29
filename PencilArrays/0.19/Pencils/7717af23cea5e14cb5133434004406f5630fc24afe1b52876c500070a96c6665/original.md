```
localgrid(p::Pencil, (x_global, y_global, ...))      -> LocalRectilinearGrid
localgrid(u::PencilArray, (x_global, y_global, ...)) -> LocalRectilinearGrid
```

Create a [`LocalRectilinearGrid`](@ref LocalGrids.LocalRectilinearGrid) from a decomposition configuration and from a set of orthogonal global coordinates `(x_global, y_global, ...)`.

In this case, each `*_global` is an `AbstractVector` describing the coordinates along one dimension of the global grid.
