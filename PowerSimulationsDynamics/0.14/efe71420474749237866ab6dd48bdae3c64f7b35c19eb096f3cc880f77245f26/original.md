```
mutable struct ControlReferenceChange <: Perturbation
    time::Float64
    device::PowerSystems.DynamicInjection
    signal::Symbol
    ref_value::Float64
end
```

A ControlReferenceChange allows to change the reference setpoint provided by a generator/inverter.

# Arguments:

  * `time::Float64` : Defines when the Control Reference Change will happen. This time should be inside the time span considered in the Simulation
  * `device::Type{<:PowerSystems.DynamicInjection}` : Dynamic device modified
  * `signal::Symbol` : determines which reference setpoint will be modified. The accepted signals are:

      * `:P_ref`: Modifies the active power reference setpoint.
      * `:V_ref`: Modifies the voltage magnitude reference setpoint (if used).
      * `:Q_ref`: Modifies the reactive power reference setpoint (if used).
      * `:ω_ref`: Modifies the frequency setpoint.
  * `ref_value::Float64` : User defined value for setpoint reference.
