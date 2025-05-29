```julia
struct HomogeneousCell{D, T, L<:Union{Nothing, Symbol}} <: LightLattices.AbstractCell{D, T}
```

  * `cell_vectors::Array{StaticArraysCore.SVector{D, T}, 1} where {D, T}`: Coordinates of nodes.

  * `label::Union{Nothing, Symbol}`: Label of the cell.

Unodered homogeneous collection of nodes in `D`-dimensional space.
