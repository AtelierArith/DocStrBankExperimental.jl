```
get_forecast(params::OpenMeteo, lat, lon, period; verbose=true)
```

A function that returns the weather forecast from OpenMeteo.com

# Arguments

  * `lat`: Latitude of the location
  * `lon`: Longitude of the location
  * `period::Union{StepRange{Date, Day}, Vector{Dates.Date}}`: Period of the forecast
  * `verbose`: If `true`, print more information in case of errors or warnings.
  * `kwargs`: Additional keyword arguments passed to [`get_forecast`](@ref) (not used in this method).

# Examples

```julia
using PlantMeteo, Dates
lat = 48.8566
lon = 2.3522
period = [Dates.today(), Dates.today()+Dates.Day(3)]
params = OpenMeteo()
get_forecast(params, lat, lon, period)
```
