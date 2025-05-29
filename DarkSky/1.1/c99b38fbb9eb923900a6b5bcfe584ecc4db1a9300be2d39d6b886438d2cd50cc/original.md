```
forecast(latitude::Float64, longitude::Float64; verbose::Bool=true, kwargs...)
```

Make a "Forecast Request", returns the current weather forecast for the next week.

# Arguments

  * `latitude`: the latitude of a location (in decimal degrees). Positive is north, negative is south.
  * `longitude`: the longitude of a location (in decimal degrees). Positive is east, negative is west.
  * `verbose`: whether to display the HTTP request verbosely (optional).
  * `exclude`: exclude some number of data blocks from the API response (optional).
  * `extend`: when present, return hour-by-hour data for the next 168 hours, instead of the next 48 (optional).
  * `lang`: return summary properties in the desired language (optional).
  * `units`: return weather conditions in the requested units (optional).
