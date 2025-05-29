```
DataFrameRows{D<:AbstractDataFrame} <: AbstractVector{DataFrameRow}
```

Iterator over rows of an `AbstractDataFrame`, with each row represented as a `DataFrameRow`.

A value of this type is returned by the [`eachrow`](@ref) function.
