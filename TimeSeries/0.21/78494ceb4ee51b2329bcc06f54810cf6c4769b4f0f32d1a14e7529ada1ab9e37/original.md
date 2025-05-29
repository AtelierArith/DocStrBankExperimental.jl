```
TimeArray{T,N,D<:TimeType,A<:AbstractArray{T,N}} <: AbstractTimeSeries{T,N,D}
```

# Constructors

```
TimeArray(timestamp, values[, colnames, meta = nothing])
TimeArray(ta::TimeArray; timestamp, values, colnames, meta)
TimeArray(data::NamedTuple, timestamp = :datetime, meta)
TimeArray(table; timestamp::Symbol, timeparser::Callable = identity)
```

The second constructor yields a new `TimeArray` with the new given fields. Note that the unchanged fields will be shared, there aren't any copy for the underlying arrays.

The third constructor builds a `TimeArray` from a `NamedTuple`.

# Arguments

  * `timestamp::AbstractVector{<:TimeType}`: a vector of sorted timestamps,
  * `timestamp::Symbol`: the column name of the time index from the source table. The constructor is used for the Tables.jl package integration.
  * `values::AbstractArray`: a data vector or matrix. Its number of rows should match the length of `timestamp`.
  * `colnames::Vector{Symbol}`: the column names. Its length should match the column of `values`.
  * `meta::Any`: a user-defined metadata.
  * `timeparser::Callable`: a mapping function for converting the source time index. For instance, `Dates.unix2datetime` is a common case.

# Examples

```
data = (datetime = [DateTime(2018, 11, 21, 12, 0), DateTime(2018, 11, 21, 13, 0)],
        col1 = [10.2, 11.2],
        col2 = [20.2, 21.2],
        col3 = [30.2, 31.2])
ta = TimeArray(data; timestamp = :datetime, meta = "Example")
```
