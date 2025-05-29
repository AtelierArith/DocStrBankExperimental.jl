```
mutable struct SourceBusVoltageChange <: Perturbation
    time::Float64
    device::PSY.Source
    signal::Symbol
    ref_value::Float64
end
```

A `SourceBusVoltageChange` allows to change the reference setpoint provided by a voltage source.

# Arguments:

  * `time::Float64` : Defines when the Control Reference Change will happen. This time should be inside the time span considered in the Simulation
  * `device::Type{<:PowerSystems.Source}` : Device modified
  * `signal::Symbol` : determines which reference setpoint will be modified. The accepted signals are:

      * :V_ref Modifies the internal voltage magnitude reference setpoint.
      * :θ_ref  Modifies the internal voltage angle reference setpoint.
  * `ref_value::Float64` : User defined value for setpoint reference.
