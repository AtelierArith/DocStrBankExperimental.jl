```
mutable struct GeneratorTrip <: Perturbation
    time::Float64
    device::PowerSystems.DynamicInjection
end
```

A `GeneratorTrip` allows to disconnect a Dynamic Generation unit from the system at a specified time.

# Arguments:

  * `time::Float64` : Defines when the Generator Trip will happen. This time should be inside the time span considered in the Simulation
  * `device::Type{<:PowerSystems.DynamicInjection}` : Device to be disconnected
