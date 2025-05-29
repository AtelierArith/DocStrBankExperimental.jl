```
mutable struct SaturationOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    kw::Float64
    ext::Dict{String, Any}
end
```

Parameters of Saturation Current Controller Limiter. Regulates the magnitude of the inverter output current, and applies a closed loop feedback regulated by a static gain which provides ant-windup

# Arguments

  * `I_max::Float64`: Maximum limit on current controller input current (device base), validation range: `(0, nothing)`
  * `kw::Float64`: Defined feedback gain, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`)
