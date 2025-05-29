```
getcoordinates!(x::Vector{<:Vec}, grid::AbstractGrid, idx::Union{Int,CellIndex})
getcoordinates!(x::Vector{<:Vec}, grid::AbstractGrid, cell::AbstractCell)
```

Mutate `x` to the coordinates of the cell corresponding to `idx` or `cell`.
