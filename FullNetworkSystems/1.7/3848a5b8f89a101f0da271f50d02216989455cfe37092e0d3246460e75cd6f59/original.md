```julia
struct GeneratorTimeSeries
```

Generator related time series data that is needed for both the day-ahead and real-time formulations. Values given in `pu` assume a base power of 100MW.

Fields:

  * `initial_generation::AxisKeys.KeyedArray{Float64, 1}`: Generation of the generator at the start of the time period (pu)
  * `offer_curve::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: Generator offer curves. `KeyedArray` where the axis keys are `generator names x datetimes`
  * `regulation_min::AxisKeys.KeyedArray{Float64, 2}`: Generator minimum output in the ancillary services market (pu)
  * `regulation_max::AxisKeys.KeyedArray{Float64, 2}`: Generator maximum output in the ancillary services market (pu)
  * `pmin::AxisKeys.KeyedArray{Float64, 2}`: Generator minimum output (pu)
  * `pmax::AxisKeys.KeyedArray{Float64, 2}`: Generator maximum output (pu)
  * `regulation_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: Ancillary services regulation reserve offer prices ($ /pu). Generators not providing the service will have `missing` offer data.

  * `spinning_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: Ancillary services spinning reserve offer prices ($ /pu). Generators not providing the service will have `missing` offer data.

  * `on_supplemental_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: Ancillary services online supplemental reserve offer prices ($ /pu). Generators not providing the service will have `missing` offer data.

  * `off_supplemental_offers::AxisKeys.KeyedArray{Union{Missing, Float64}, 2}`: Ancillary services offline supplemental reserve offer prices ($ /pu). Generators not providing the service will have `missing` offer data.
