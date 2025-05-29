```
TimeArray{T,V} <: AbstractTimeArray{T,V}
```

Type describing a time series with timestamps of type `T` and values of type `V`.

## Fields

  * `values::Vector{TimeTick{T,V}}`: Elements of a time series.
  * `length::Int64`: The length of the underlying array.

## Accessors

  * `ta_values(x::TimeArray)` -> `x.values`
