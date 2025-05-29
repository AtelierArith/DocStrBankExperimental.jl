```julia
struct JumpSystem{U<:RecursiveArrayTools.ArrayPartition} <: ModelingToolkit.AbstractTimeDependentSystem
```

A system of jump processes.

# Fields

  * `tag`: A tag for the system. If two systems have the same tag, then they are structurally identical.

  * `eqs`: The jumps of the system. Allowable types are `ConstantRateJump`, `VariableRateJump`, `MassActionJump`.

  * `iv`: The independent variable, usually time.
  * `unknowns`: The dependent variables, representing the state of the system.  Must not contain the independent variable.
  * `ps`: The parameters of the system. Must not contain the independent variable.
  * `var_to_name`: Array variables.
  * `observed`: Observed equations.
  * `name`: The name of the system.
  * `description`: A description of the system.
  * `systems`: The internal systems. These are required to have unique names.
  * `defaults`: The default values to use when initial conditions and/or parameters are not supplied in `ODEProblem`.

  * `guesses`: The guesses to use as the initial conditions for the initialization system.

  * `initializesystem`: The system for performing the initialization.

  * `initialization_eqs`: Extra equations to be enforced during the initialization sequence.

  * `connector_type`: Type of the system.

  * `continuous_events`: A `Vector{SymbolicContinuousCallback}` that model events. The integrator will use root finding to guarantee that it steps at each zero crossing.

  * `discrete_events`: A `Vector{SymbolicDiscreteCallback}` that models events. Symbolic analog to `SciMLBase.DiscreteCallback` that executes an affect when a given condition is true at the end of an integration step. Note, one must make sure to call `reset_aggregated_jumps!(integrator)` if using a custom affect function that changes any unknown value or parameter.

  * `parameter_dependencies`: Topologically sorted parameter dependency equations, where all symbols are parameters and the LHS is a single parameter.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `gui_metadata`: Metadata for MTK GUI.

  * `namespacing`: If false, then `sys.x` no longer performs namespacing.

  * `complete`: If true, denotes the model will not be modified any further.

  * `index_cache`: Cached data for fast symbolic indexing.

  * `isscheduled`

# Example

```julia
using ModelingToolkit, JumpProcesses
using ModelingToolkit: t_nounits as t

@parameters β γ
@variables S(t) I(t) R(t)
rate₁   = β*S*I
affect₁ = [S ~ S - 1, I ~ I + 1]
rate₂   = γ*I
affect₂ = [I ~ I - 1, R ~ R + 1]
j₁      = ConstantRateJump(rate₁,affect₁)
j₂      = ConstantRateJump(rate₂,affect₂)
j₃      = MassActionJump(2*β+γ, [R => 1], [S => 1, R => -1])
@named js      = JumpSystem([j₁,j₂,j₃], t, [S,I,R], [β,γ])
```
