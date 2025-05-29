```
get_weather(lat, lon, period::Union{StepRange{Date, Day}, Vector{Dates.Date}}; api::DataType=OpenMeteo, sink=TimeStepTable, kwargs...)
```

Returns the weather forecast for a given location and time using a weather API.

# Arguments

  * `lat::Float64`: Latitude of the location in degrees
  * `lon::Float64`: Longitude of the location in degrees
  * `period::Union{StepRange{Date, Day}, Vector{Dates.Date}}`: Period of the forecast
  * `api::DataType=OpenMeteo`: API to use for the forecast.
  * `sink::DataType=TimeStepTable`: Type of the output. Default is `TimeStepTable`, but it

can be any type that implements the `Tables.jl` interface, such as `DataFrames`.

  * `kwargs...`: Additional keyword arguments that are passed to the API

# Details

We can get all available APIs using `subtype(AbstractAPI)`. Please keep in mind that the default [`OpenMeteo`](@ref) API is not free for commercial use, and that you should use it responsibly.

# Examples

```julia
using PlantMeteo, Dates
# Forecast for today and tomorrow:
period = [today(), today()+Dates.Day(1)]
w = get_weather(48.8566, 2.3522, period)
```
