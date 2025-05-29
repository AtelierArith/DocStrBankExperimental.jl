```
mutable struct EggMortalityRossi <: TemperatureResponse
    a::Float64
    b::Float64
end
```

Data for `μ_temperature_response`. `Species`: AedesAegypti, `LifeStage`: Egg. Source: Rossi et al (2014).

# Arguments

  * `a::Float64`: Death rate at low temperatures, validation range: `(0, nothing)`
  * `b::Float64`: Influence factor of temperature, validation range: `(0, nothing)`
