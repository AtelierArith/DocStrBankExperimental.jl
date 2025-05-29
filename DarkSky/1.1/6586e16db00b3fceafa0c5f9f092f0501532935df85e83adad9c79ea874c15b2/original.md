```
forecast(latitude::Float64, longitude::Float64, time::DateTime; verbose::Bool=true, kwargs...)
```

Make a "Time Machine Request", returns the observed or forecast weather conditions for a date in the past or future.

# Arguments

  * `latitude`: the latitude of a location (in decimal degrees). Positive is north, negative is south.
  * `longitude`: the longitude of a location (in decimal degrees). Positive is east, negative is west.
  * `time`: the timestamp for a Time Machine Request (optional).
  * `verbose`: whether to display the HTTP request verbosely (optional).
  * `exclude`: exclude some number of data blocks from the API response (optional).
  * `lang`: return summary properties in the desired language (optional).
  * `units`: return weather conditions in the requested units (optional).
