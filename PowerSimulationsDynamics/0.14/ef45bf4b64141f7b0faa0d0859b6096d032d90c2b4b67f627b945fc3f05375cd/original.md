```
mutable struct LoadTrip <: Perturbation
    time::Float64
    device::PowerSystems.ElectricLoad
end
```

A `LoadTrip` allows the user to disconnect a load from the system.

# Arguments:

  * `time::Float64` : Defines when the Generator Trip will happen. This time should be inside the time span considered in the Simulation
  * `device::Type{<:PowerSystems.ElectricLoad}` : Device to be disconnected
