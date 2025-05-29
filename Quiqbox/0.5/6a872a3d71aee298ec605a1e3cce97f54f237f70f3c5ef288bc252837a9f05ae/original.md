```
GridBox{T, D, NP, GPT<:SpatialPoint{T, D}} <: SpatialStructure{T, D}
```

A container of multiple `D`-dimensional grid points.

≡≡≡ Field(s) ≡≡≡

`spacing::NTuple{D, T}`: The distance between adjacent grid points along each dimension.

`nPoint::Int`: Total number of the grid points.

`point::NTuple{NP, GPT}`: The grid points represented by [`SpatialPoint`](@ref).

`param::Tuple{Vararg{ParamBox{T}}}`: All the parameters in the `GridBox`.

≡≡≡ Initialization Method(s) ≡≡≡

```
GridBox(nGrids::NTuple{D, Int}, spacing::NTuple{D, Union{Array{T, 0}, T}}, 
        center::Union{AbstractVector{T}, NTuple{D, T}}=ntuple(_->T(0),Val(D)); 
        canDiff::NTuple{D, Bool}=ntuple(_->true, Val(D)), 
        index::NTuple{D, Int}=ntuple(_->0, Val(D))) where {T<:AbstractFloat, D} -> 
GridBox{T, D}

GridBox(nGrids::NTuple{D, Int}, spacingForAllDim::Union{T, Array{T, 0}}, 
        center::Union{AbstractVector{T}, NTuple{D, T}}=ntuple(_->T(0), Val(D)); 
        canDiff::Bool=true, index::Int=0) where {T<:AbstractFloat, D} -> 
GridBox{T, D}
```

Construct a general `D`-dimensional `GridBox`.

=== Positional argument(s) ===

`nGrids::NTuple{D, Int}`: The numbers of grids along each dimension.

`spacing::NTuple{D, Union{Array{T, 0}, T}}`: The spacing between grid points along each  dimension.

`spacingForAllDim::NTuple{D, Union{Array{T, 0}, T}}`: A single spacing applied for all  dimensions.

`center::Union{AbstractVector{T}, NTuple{D, T}}`: The coordinate of the geometric center of  the grid box.

=== Keyword argument(s) ===

`canDiff`::NTuple{D, Bool}: Whether the `ParamBox`es of each dimension stored in the  constructed `GridBox` will be marked as differentiable.

`index`::NTuple{D, Int}: The Index(s) that will be assigned to the shared input variable(s)  `L` of the stored `ParamBox`es.
