```
struct ParameterTimeseriesCollection{T}
function ParameterTimeseriesCollection(collection)
```

A utility struct that helps in storing multiple parameter timeseries. It expects a collection of timseries objects ([`is_timeseries`](@ref) returns [`Timeseries`](@ref)) for each. Each of the timeseries objects should implement [`state_values`](@ref) and [`current_time`](@ref). Effectively, the "states" of each contained timeseries object are the parameter values it stores the timeseries of.

The collection is expected to implement `Base.eachindex`, `Base.iterate` and `Base.getindex`. The indexes of the collection should agree with the timeseries indexes returned by calling [`timeseries_parameter_index`](@ref) on the corresponding index provider.

This type forwards `eachindex`, `iterate` and `length` to the contained `collection`. It implements `Base.parent` to allow access to the contained `collection`, and has the following `getindex` methods:

  * `getindex(ptc::ParameterTimeseriesCollection, idx) = ptc.collection[idx]`.
  * `getindex(::ParameterTimeseriesCollection, idx::ParameterTimeseriesIndex)` returns the timeseries of the parameter referred to by `idx`.
  * `getindex(::ParameterTimeseriesCollection, idx::ParameterTimeseriesIndex, subidx)` returns the value of the parameter referred to by `idx` at the time index `subidx`.
  * Apart from these cases, if multiple indexes are provided the first is treated as a timeseries index, the second the time index in the timeseries, and the (optional) third the index of the parameter in an element of the timeseries.

The three-argument version of [`parameter_values`](@ref) is implemented for this type. The single-argument version of `parameter_values` returns the cached parameter object. This type does not implement any traits.
