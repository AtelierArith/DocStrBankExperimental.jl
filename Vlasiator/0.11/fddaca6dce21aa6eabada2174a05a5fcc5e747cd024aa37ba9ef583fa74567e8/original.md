```
refineslice(meta, idlist::Vector{Int}, data::AbstractVector, normal::Symbol) -> Vector
refineslice(meta, idlist::Vector{Int}, data::AbstractMatrix, normal::Symbol) -> Matrix
refineslice(meta, idlist::Vector{Int}, data::AbstractArray, dir::Int)
```

Generate data on the finest refinement level given cellids `idlist` and variable `data` on the slice perpendicular to `normal`. If `data` is 2D, then the first dimension is treated as vector components.
