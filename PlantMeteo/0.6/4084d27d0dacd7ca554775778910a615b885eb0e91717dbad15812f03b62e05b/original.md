```
OpenMeteoUnits(temperature_unit, windspeed_unit, precipitation_unit)
OpenMeteoUnits(;temperature_unit="celsius", windspeed_unit="ms", precipitation_unit="mm")
```

A type that defines the units used for the variabels when calling the [open-meteo.com](https://open-meteo.com/) API.

# Arguments

  * `temperature_unit`: the temperature unit, can be "celsius" or "fahrenheit". Default to "celsius".
  * `windspeed_unit`: the windspeed unit, can be "ms", "kmh", "mph", or "kn". Default to "ms".
  * `precipitation_unit`: the precipitation unit, can be "mm" or "inch". Default to "mm".

# Examples

```jldoctest
julia> units = OpenMeteoUnits("celsius", "ms", "mm")
OpenMeteoUnits("celsius", "ms", "mm")
```
