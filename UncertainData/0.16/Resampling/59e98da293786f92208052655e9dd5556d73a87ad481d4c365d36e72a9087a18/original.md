```
resample!(v::AbstractArray{T, 1}, x::AbstractUncertainValue)
resample!(v::MVector{N, T}, x::AbstractUncertainValue) where {N, T}
resample!(v::FieldVector{N, T}, x::AbstractUncertainValue) where {N, T}

resample!(v::MVector{N, T}, x::Vararg{AbstractUncertainValue, N}) where {N, T}
resample!(v::FieldVector{N, T}, x::Vararg{AbstractUncertainValue, N}) where {N, T}

resample!(v::AbstractArray{T, 1}, x::UVAL_COLLECTION_TYPES) where T
resample!(v::AbstractArray{T, 2}, x::UVAL_COLLECTION_TYPES) where T

resample!(idxs::AbstractArray{T, 1}, vals::AbstractArray{T, 1}, 
    x::AbstractUncertainIndexValueDataset) where T
resample!(idxs::AbstractArray{T, 2}, vals::AbstractArray{T, 2}, 
    x::AbstractUncertainIndexValueDataset) where T
```

Resample a uncertain value `x`, or a collection of uncertain values `x`, into a  pre-allocated container `v`.

## Uncertain values

  * If `x` is a single uncertain value, and `v` is vector-like, then fill    `v` with `N` draws of `x`. Works with vectors of length `N`,    `MVector{N, T}`s or `FieldVector{N, T}`s.

## Uncertain collections

Uncertain collections may be a `Vector{AbstractUncertainValue}` of length `N`,  an  `AbstractUncertainValueDataset`, or an `NTuple{N, AbstractUncertainValue}`. See also [`UVAL_COLLECTION_TYPES`](@ref).

  * If `x` is a collection of uncertain values and `v` is vector-like, then    fill `v[i]` with a draw of `x[i]` for `i = 1:N`.
  * If `x` is a collection of uncertain values and `v` is a 2D-array, then    fill the `i`-th column of `v` with `length(x)` draws of the `i`-th    uncertain value in `x`.

## Uncertain index-value collections

  * If two mutable vector-like containers, `idxs` and `vals`, are provided along    with an uncertain index-value dataset `x`, then fill `idxs[i]` with a    random draw from `x.indices[i]` and fill `vals[i]` with a random draw    from `x.values[i]`.
  * If two mutable matrix-like containers, `idxs` and `vals` are provided along   with an uncertain index-value dataset `x` (where the number of    columns in both `idxs` and `vals` matches `length(x)`), then fill the    `i`-th column of `idxs` with `size(idxs, 1)` draws from `x.indices[i]`,   and fill the `i`-th column of `vals` with `size(idxs, 1)` draws    from `x.values[i]`.
