```
add_fault!(data::Dict{String,Any}, name::String, type::String, bus::String, connections::Vector{Int}, resistance::Real, phase_resistance::Real)
```

Creates a fault dictionary given the `type` of fault, i.e., one of "3p", "ll", "lg", the `bus` on which the fault is active, the `connections` on which the fault applies, the `resistance` between the phase and ground, in the case of "lg", or phase and phase, and adds it to `data["fault"]` under `"name"`
