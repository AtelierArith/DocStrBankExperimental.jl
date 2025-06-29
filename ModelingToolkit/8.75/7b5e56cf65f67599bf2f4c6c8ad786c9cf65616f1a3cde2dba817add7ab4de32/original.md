```julia
struct DiscreteSystem <: ModelingToolkit.AbstractTimeDependentSystem
```

A system of difference equations.

# Fields

  * `tag`: A tag for the system. If two systems have the same tag, then they are structurally identical.

  * `eqs`: The differential equations defining the discrete system.
  * `iv`: Independent variable.
  * `states`: Dependent (state) variables. Must not contain the independent variable.
  * `ps`: Parameter variables. Must not contain the independent variable.
  * `tspan`: Time span.
  * `var_to_name`: Array variables.
  * `ctrls`: Control parameters (some subset of `ps`).
  * `observed`: Observed states.
  * `name`: The name of the system

  * `systems`: The internal systems. These are required to have unique names.

  * `defaults`: The default values to use when initial conditions and/or parameters are not supplied in `DiscreteProblem`.

  * `preface`: Inject assignment statements before the evaluation of the RHS function.

  * `connector_type`: Type of the system.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `gui_metadata`: Metadata for MTK GUI.

  * `tearing_state`: Cache for intermediate tearing state.

  * `substitutions`: Substitutions generated by tearing.

  * `complete`: If a model `sys` is complete, then `sys.x` no longer performs namespacing.

  * `parent`: The hierarchical parent system before simplification.

# Example

```
using ModelingToolkit

@parameters σ=28.0 ρ=10.0 β=8/3 δt=0.1
@variables t x(t)=1.0 y(t)=0.0 z(t)=0.0
D = Difference(t; dt=δt)

eqs = [D(x) ~ σ*(y-x),
       D(y) ~ x*(ρ-z)-y,
       D(z) ~ x*y - β*z]

@named de = DiscreteSystem(eqs,t,[x,y,z],[σ,ρ,β]; tspan = (0, 1000.0)) # or
@named de = DiscreteSystem(eqs)
```
