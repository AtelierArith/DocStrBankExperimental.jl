```
mutable struct LoadChange <: Perturbation
    time::Float64
    device::PowerSystems.ElectricLoad
    signal::Symbol
    ref_value::Float64
end
```

A LoadChange allows to change the active or reactive power setpoint from a load.

# Arguments:

  * `time::Float64` : Defines when the Load Change will happen. This time should be inside the time span considered in the Simulation
  * `device::Type{<:PowerSystems.ElectricLoad}` : Dynamic device modified
  * `signal::Symbol` : determines which reference setpoint will be modified. The accepted signals are:

      * `:P_ref`: Modifies the active power reference setpoint.
      * `:Q_ref`: Modifies the reactive power reference setpoint.
  * `ref_value::Float64` : User defined value for setpoint reference.
