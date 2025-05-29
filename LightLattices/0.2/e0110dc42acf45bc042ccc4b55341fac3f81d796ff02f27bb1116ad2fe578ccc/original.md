```julia
struct InhomogeneousCell{D, T, N, L<:Union{Nothing, Symbol}, T′} <: LightLattices.AbstractCell{D, T}
```

  * `cell_vectors::RecursiveArrayTools.ArrayPartition{T′, NTuple{N, Array{StaticArraysCore.SVector{D, T}, 1}}} where {D, T, N, T′}`: Coordinates of nodes.

  * `group_sizes::NTuple{N, Int64} where N`: Sizes of the homogeneous groups inside inhomogeneous cell.

  * `label::Union{Nothing, Symbol}`: Label of the cell.

Unordered inhomogeneous collection of nodes in `D`-dimensional space. This type allows one to partition the nodes of the cell into several groups. Different groups of nodes may correspond to the different classes of physical objects occupying these nodes.
