```
SimpleAtmosphere{<:Number,<:StabilityClass}(kwargs...)<:Atmosphere
```

A simple model of the atmosphere.

# Arguments

  * `pressure::Number=101325`: atmospheric pressure, Pa
  * `temperature::Number=298.15`: ambient pressure, K
  * `windspeed::Number=1.5`: windspeed at anemometer height, m/s
  * `windspeed_height::Number=10`: anemometer height, m
  * `rel_humidity::Number=0`: relative humidity, %
  * `stability::StabilityClass=ClassF`: Pasquill-Gifford stability class
