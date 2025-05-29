```
setup_reservoir_state(model, <keyword arguments>)
# Ex: For immiscible two-phase
setup_reservoir_state(model, Pressure = 1e5, Saturations = [0.2, 0.8])
```

Convenience constructor that initializes a state for a `MultiModel` set up using [`setup_reservoir_model`](@ref). The main convenience over [`setup_state`](@ref) is only the reservoir initialization values need be provided: wells are automatically initialized from the connected reservoir cells.

As an alternative to passing keyword arguments, a `Dict{Symbol, Any}` instance can be sent in as a second, non-keyword argument.
