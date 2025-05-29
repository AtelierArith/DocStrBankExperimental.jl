```julia
struct JumpSystem{U<:RecursiveArrayTools.ArrayPartition} <: ModelingToolkit.AbstractTimeDependentSystem
```

A system of jump processes.

# Fields

  * `tag`: A tag for the system. If two systems have the same tag, then they are structurally identical.

  * `eqs`: The jumps of the system. Allowable types are `ConstantRateJump`, `VariableRateJump`, `MassActionJump`.

  * `iv`: The independent variable, usually time.
  * `states`: The dependent variables, representing the state of the system.  Must not contain the independent variable.
  * `ps`: The parameters of the system. Must not contain the independent variable.
  * `var_to_name`: Array variables.
  * `observed`: Observed states.
  * `name`: The name of the system.
  * `systems`: The internal systems. These are required to have unique names.
  * `defaults`: The default values to use when initial conditions and/or parameters are not supplied in `ODEProblem`.

  * `connector_type`: Type of the system.

  * `discrete_events`: A `Vector{SymbolicDiscreteCallback}` that models events. Symbolic analog to `SciMLBase.DiscreteCallback` that executes an affect when a given condition is true at the end of an integration step. Note, one must make sure to call `reset_aggregated_jumps!(integrator)` if using a custom affect function that changes any state value or parameter.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `gui_metadata`: Metadata for MTK GUI.

  * `complete`: If a model `sys` is complete, then `sys.x` no longer performs namespacing.

# Example

```julia
using ModelingToolkit, JumpProcesses

@parameters β γ
@variables t S(t) I(t) R(t)
rate₁   = β*S*I
affect₁ = [S ~ S - 1, I ~ I + 1]
rate₂   = γ*I
affect₂ = [I ~ I - 1, R ~ R + 1]
j₁      = ConstantRateJump(rate₁,affect₁)
j₂      = ConstantRateJump(rate₂,affect₂)
j₃      = MassActionJump(2*β+γ, [R => 1], [S => 1, R => -1])
@named js      = JumpSystem([j₁,j₂,j₃], t, [S,I,R], [β,γ])
```
