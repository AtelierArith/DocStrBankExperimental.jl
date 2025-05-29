```
build_fault_study(data::Dict; default_fault_resistance::Real=0.0001)
```

Builds a dictionary of fault studies on a transmission (single-phase positive sequence) network that are intended to be used in conjunction with [`solve_fault_study`](@ref solve_fault_study).

The function will iterate over all buses and create faults using the default fault resistance. The fault study dictionary will have the following structure:

```julia
    Dict{String,Any}(
        "bus_i" => Dict{String,Any}(
            "fault_bus" => bus_i
            "gf" => 1 / resistance,
            "status" => 1
        ),
        ...
    )
```
