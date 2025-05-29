```
aligntime(col::AbstractArray, time::ScaledArrOrSub)
aligntime(col::AbstractArray, time::RotatingTimeArray)
aligntime(data, colname::Union{Symbol,Integer}, timename::Union{Symbol,Integer})
```

Convert a column of time values `col` to a [`ScaledArray`](@ref) with a `pool` that has the same first element and step size as the `pool` from the [`ScaledArray`](@ref) `time`. If `time` is a [`RotatingTimeArray`](@ref) with the `time` field being a [`ScaledArray`](@ref), the returned array is also a [`RotatingTimeArray`](@ref) with the `time` field being the converted [`ScaledArray`](@ref). Alternative, the arrays may be specified with a `Tables.jl`-compatible `data` table and column indices `colname` and `timename`. See also [`settime`](@ref).

This is useful for representing all discretized time periods with the same scale so that the underlying reference values returned by `DataAPI.refarray` can be directly comparable across the columns.
