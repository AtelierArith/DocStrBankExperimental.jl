```
function initlogiset(
    dataset::AbstractDimensionalDataset,
    features::AbstractVector;
    worldtype_by_dim::Union{Nothing,AbstractDict{Int,Type{<:AbstractWorld}}}=nothing
)::UniformFullDimensionalLogiset
```

Given an [`AbstractDimensionalDataset`](@ref), build a [`UniformFullDimensionalLogiset`](@ref).

# Keyword Arguments

  * worldtype*by*dim::Union{Nothing,AbstractDict{Int,Type{<:AbstractWorld}}}=nothing:

map between a dimensionality, as integer, and the [`AbstractWorld`](@ref) type associated; when unspecified, this is defaulted to `0 => OneWorld, 1 => Interval, 2 => Interval2D`.

See also [`AbstractDimensionalDataset`](@ref), SoleLogics.AbstractWorld, MultiData.dimensionality, [`UniformFullDimensionalLogiset`](@ref).
