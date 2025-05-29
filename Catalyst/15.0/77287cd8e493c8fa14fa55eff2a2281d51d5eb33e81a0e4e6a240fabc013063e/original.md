```julia
struct ReactionSystem{V<:Catalyst.NetworkProperties} <: ModelingToolkit.AbstractTimeDependentSystem
```

A system of chemical reactions.

# Fields

  * `eqs`: The equations (reactions and algebraic/differential) defining the system.
  * `rxs`: The Reactions defining the system.
  * `iv`: Independent variable (usually time).
  * `sivs`: Spatial independent variables
  * `unknowns`: All dependent (unknown) variables, species and non-species. Must not contain the independent variable.
  * `species`: Dependent unknown variables representing species
  * `ps`: Parameter variables. Must not contain the independent variable.
  * `var_to_name`: Maps Symbol to corresponding variable.
  * `observed`: Equations for observed variables.
  * `name`: The name of the system
  * `systems`: Internal sub-systems
  * `defaults`: The default values to use when initial conditions and/or parameters are not supplied in `ODEProblem`.

  * `connection_type`: Type of the system
  * `networkproperties`: `NetworkProperties` object that can be filled in by API functions. INTERNAL – not considered part of the public API.
  * `combinatoric_ratelaws`: Sets whether to use combinatoric scalings in rate laws. true by default.
  * `continuous_events`: continuous_events: A `Vector{SymbolicContinuousCallback}` that model events. The integrator will use root finding to guarantee that it steps at each zero crossing.

  * `discrete_events`: discrete_events: A `Vector{SymbolicDiscreteCallback}` that models events. Symbolic analog to `SciMLBase.DiscreteCallback` that executes an affect when a given condition is true at the end of an integration step.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `complete`: complete: if a model `sys` is complete, then `sys.x` no longer performs namespacing.

  * `parent`: The hierarchical parent system before simplification that MTK now seems to require for hierarchical namespacing to work in indexing.

# Example

Continuing from the example in the [`Reaction`](@ref) definition:

```julia
# simple constructor that infers species and parameters
@named rs = ReactionSystem(rxs, t)

# allows specification of species and parameters
@named rs = ReactionSystem(rxs, t, [A,B,C,D], k)
```

Keyword Arguments:

  * `observed::Vector{Equation}`, equations specifying observed variables.
  * `systems::Vector{AbstractSystems}`, vector of sub-systems. Can be `ReactionSystem`s, `ODESystem`s, or `NonlinearSystem`s.
  * `name::Symbol`, the name of the system (must be provided, or `@named` must be used).
  * `defaults::Dict`, a dictionary mapping parameters to their default values and species to their default initial values.
  * `checks = true`, boolean for whether to check units.
  * `networkproperties = NetworkProperties()`, cache for network properties calculated via API functions.
  * `combinatoric_ratelaws = true`, sets the default value of `combinatoric_ratelaws` used in calls to `convert` or calling various problem types with the `ReactionSystem`.
  * `balanced_bc_check = true`, sets whether to check that BC species appearing in reactions are balanced (i.e appear as both a substrate and a product with the same stoichiometry).

Notes:

  * ReactionSystems currently do rudimentary unit checking, requiring that all species have the same units, and all reactions have rate laws with units of (species units) / (time units). Unit checking can be disabled by passing the keyword argument `checks=false`.
