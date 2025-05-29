```
mutable struct HybridOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    rv::Float64
    lv::Float64
    ext::Dict{String, Any}
end
```

Parameters of Hybrid Current Controller Limiter. Regulates the magnitude of the inverter output current, but with a closed loop feedback regulated by a virtual impedance which provides ant-windup. Described in: Novel Hybrid Current Limiter for Grid-Forming Inverter Control During Unbalanced Faults by Baeckland and Seo, 2023 

# Arguments

  * `I_max::Float64`: Maximum limit on current controller input current (device base), validation range: `(0, nothing)`
  * `rv::Float64`: Real part of the virtual impedance, validation range: `(0, nothing)`
  * `lv::Float64`: Imaginary part of the virtual impedance, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`)
