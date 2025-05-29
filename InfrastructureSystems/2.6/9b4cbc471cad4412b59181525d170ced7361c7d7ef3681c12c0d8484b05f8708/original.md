Supertype for keys that can be used to access a desired time series dataset

Concrete subtypes:

  * [`StaticTimeSeriesKey`](@ref)
  * [`ForecastKey`](@ref)

Required methods:

  * `get_name`
  * `get_resolution`
  * `get_time_series_type`

The default methods rely on the field names `name` and `time_series_type`.
