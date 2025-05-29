```julia
struct SDESystem <: ModelingToolkit.AbstractODESystem
```

A system of stochastic differential equations.

# Fields

  * `tag`: A tag for the system. If two systems have the same tag, then they are structurally identical.

  * `eqs`: The expressions defining the drift term.
  * `noiseeqs`: The expressions defining the diffusion term.
  * `iv`: Independent variable.
  * `unknowns`: Dependent variables. Must not contain the independent variable.
  * `ps`: Parameter variables. Must not contain the independent variable.
  * `tspan`: Time span.
  * `var_to_name`: Array variables.
  * `ctrls`: Control parameters (some subset of `ps`).
  * `observed`: Observed equations.
  * `tgrad`: Time-derivative matrix. Note: this field will not be defined until [`calculate_tgrad`](@ref) is called on the system.

  * `jac`: Jacobian matrix. Note: this field will not be defined until [`calculate_jacobian`](@ref) is called on the system.

  * `ctrl_jac`: Control Jacobian matrix. Note: this field will not be defined until [`calculate_control_jacobian`](@ref) is called on the system.

  * `Wfact`: Note: this field will not be defined until [`generate_factorized_W`](@ref) is called on the system.

  * `Wfact_t`: Note: this field will not be defined until [`generate_factorized_W`](@ref) is called on the system.

  * `name`: The name of the system.

  * `description`: A description of the system.

  * `systems`: The internal systems. These are required to have unique names.

  * `defaults`: The default values to use when initial conditions and/or parameters are not supplied in `ODEProblem`.

  * `guesses`: The guesses to use as the initial conditions for the initialization system.

  * `initializesystem`: The system for performing the initialization.

  * `initialization_eqs`: Extra equations to be enforced during the initialization sequence.

  * `connector_type`: Type of the system.

  * `continuous_events`: A `Vector{SymbolicContinuousCallback}` that model events. The integrator will use root finding to guarantee that it steps at each zero crossing.

  * `discrete_events`: A `Vector{SymbolicDiscreteCallback}` that models events. Symbolic analog to `SciMLBase.DiscreteCallback` that executes an affect when a given condition is true at the end of an integration step.

  * `parameter_dependencies`: Topologically sorted parameter dependency equations, where all symbols are parameters and the LHS is a single parameter.

  * `assertions`: Mapping of conditions which should be true throughout the solution process to corresponding error messages. These will be added to the equations when calling `debug_system`.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `gui_metadata`: Metadata for MTK GUI.

  * `namespacing`: If false, then `sys.x` no longer performs namespacing.

  * `complete`: If true, denotes the model will not be modified any further.

  * `index_cache`: Cached data for fast symbolic indexing.

  * `parent`: The hierarchical parent system before simplification.

  * `is_scalar_noise`: Signal for whether the noise equations should be treated as a scalar process. This should only be `true` when `noiseeqs isa Vector`.

  * `is_dde`: A boolean indicating if the given `ODESystem` represents a system of DDEs.

  * `isscheduled`
  * `tearing_state`

# Example

```julia
using ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D

@parameters σ ρ β
@variables x(t) y(t) z(t)

eqs = [D(x) ~ σ*(y-x),
       D(y) ~ x*(ρ-z)-y,
       D(z) ~ x*y - β*z]

noiseeqs = [0.1*x,
            0.1*y,
            0.1*z]

@named de = SDESystem(eqs,noiseeqs,t,[x,y,z],[σ,ρ,β]; tspan = (0, 1000.0))
```
