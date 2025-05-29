```
add_fault!(data::Dict{String,Any}, name::String, type::String, bus::String, connections::Vector{Int}, resistance::Real)
```

Creates a fault dictionary given the `type` of fault, i.e., one of "3pq", "llg", the `bus` on which the fault is active, the `connections` on which the fault applies, the `resistance` between the phase and ground, and the `phase_resistance` between phases, and adds it to `data["fault"]` under `"name"`
