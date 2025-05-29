```
DynamicalSystem
```

`DynamicalSystem` is an abstract supertype encompassing all concrete implementations of what counts as a "dynamical system" in the DynamicalSystems.jl library.

***All concrete implementations of `DynamicalSystem` can be iteratively evolved in time via the [`step!`](@ref) function.*** Hence, most library functions that evolve the system will mutate its current state and/or parameters. See the documentation online for implications this has for parallelization.

`DynamicalSystem` is further separated into two abstract types: `ContinuousTimeDynamicalSystem, DiscreteTimeDynamicalSystem`. The simplest and most common concrete implementations of a `DynamicalSystem` are [`DeterministicIteratedMap`](@ref) or [`CoupledODEs`](@ref).

## Description

A `DynamicalSystem` **represents the time evolution of a state in a state space**. It mainly encapsulates three things:

1. A state, typically referred to as `u`, with initial value `u0`. The space that `u` occupies is the state space of `ds` and the length of `u` is the dimension of `ds` (and of the state space).
2. A dynamic rule, typically referred to as `f`, that dictates how the state evolves/changes with time when calling the [`step!`](@ref) function. `f` is typically a standard Julia function, see the online documentation for examples.
3. A parameter container `p` that parameterizes `f`. `p` can be anything, but in general it is recommended to be a type-stable mutable container.

In sort, any set of quantities that change in time can be considered a dynamical system, however the concrete subtypes of `DynamicalSystem` are much more specific in their scope. Concrete subtypes typically also contain more information than the above 3 items.

In this scope dynamical systems have a known dynamic rule `f`. Finite *measured* or *sampled* data from a dynamical system are represented using [`StateSpaceSet`](@ref). Such data are obtained from the [`trajectory`](@ref) function or from an experimental measurement of a dynamical system with an unknown dynamic rule.

See also the DynamicalSystems.jl tutorial online for examples making dynamical systems.

## Integration with ModelingToolkit.jl

Dynamical systems that have been constructed from `DEProblem`s that themselves have been constructed from ModelingToolkit.jl keep a reference to the symbolic model and all symbolic variables. Accessing a `DynamicalSystem` using symbolic variables is possible via the functions [`observe_state`](@ref), [`set_state!`](@ref), [`current_parameter`](@ref) and [`set_parameter!`](@ref). The referenced MTK model corresponding to the dynamical system can be obtained with `model = referrenced_sciml_model(ds::DynamicalSystem)`.

See also the DynamicalSystems.jl tutorial online for an example.

!!! warn "Initial conditions and parameters"
    ModelingToolkit.jl treats initial conditions of all variables as additional parameters. This is because its terminology is aimed primarily at initial value problems rather than dynamical systems. It is strongly recommended when making a dynamical system from an MTK model to only access parameters via symbols, and to not use the `split = false` keyword when creating the problem type from the MTK model.


## API

The API that `DynamicalSystem` employs is composed of the functions listed below. Once a concrete instance of a subtype of `DynamicalSystem` is obtained, it can queried or altered with the following functions.

The main use of a concrete dynamical system instance is to provide it to downstream functions such as `lyapunovspectrum` from ChaosTools.jl or `basins_of_attraction` from Attractors.jl. A typical user will likely not utilize directly the following API, unless when developing new algorithm implementations that use dynamical systems.

### API - obtain information

  * `ds(t)` with `ds` an instance of `DynamicalSystem`: return the state of `ds` at time `t`. For continuous time systems this interpolates current and previous time step and is very accurate; for discrete time systems it only works if `t` is the current time.
  * [`current_state`](@ref)
  * [`initial_state`](@ref)
  * [`observe_state`](@ref)
  * [`current_parameters`](@ref)
  * [`current_parameter`](@ref)
  * [`initial_parameters`](@ref)
  * [`isdeterministic`](@ref)
  * [`isdiscretetime`](@ref)
  * [`dynamic_rule`](@ref)
  * [`current_time`](@ref)
  * [`initial_time`](@ref)
  * [`isinplace`](@ref)
  * [`successful_step`](@ref)
  * [`referrenced_sciml_model`](@ref)

### API - alter status

  * [`reinit!`](@ref)
  * [`set_state!`](@ref)
  * [`set_parameter!`](@ref)
  * [`set_parameters!`](@ref)
