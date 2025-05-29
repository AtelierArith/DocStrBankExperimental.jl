```
mutable struct SinusoidalTemperature <: Temperature
    a::Float64
    b::Int64
    c::Int64
    d::Float64
end
```

Data for simulation that features sinusoidal temperature fluctuation in °C. Uses `cosine` implementation applicable to the Southern Hemisphere. Generated internally.

# Arguments

  * `a::Float64`: Amplitude.
  * `b::Float64`: Periodicity coefficient.
  * `c::Float64`: Time period (days).
  * `d::Float64`: Mean.
