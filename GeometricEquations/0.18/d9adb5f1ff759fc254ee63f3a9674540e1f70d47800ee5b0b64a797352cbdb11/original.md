EquationProblem: stores a GeometricEquation together with initial conditions, parameters, time span and time step size.

### Parameters

  * `ST <: GeometricEquation`: super type, used for dispatch
  * `DT <: Number`: data type
  * `TT <: Real`: time step type
  * `AT <: AbstractArray{DT}`: array type of state variable
  * `equType <: GeometricEquation`: equation type
  * `functionsType <: NamedTuple`: types of all function methods
  * `solutionsType <: NamedTuple`: types of all solution methods
  * `icsType <: NamedTuple`: types of all initial conditions
  * `parType <: OptionalParameters`: parameters type

### Fields

  * `equation`: reference to the parent equation object holding the vector fields, etc.
  * `functions`: methods for all vector fields, etc., that define the problem
  * `solutions`: methods for all solutions, etc., if defined
  * `tspan`: time span for problem `(t₀,t₁)`
  * `tstep`: time step to be used in simulation
  * `ics`: `NamedTuple` containing the initial conditions, must contain one field for each state variable
  * `parameters`: either a `NamedTuple` containing the equation's parameters or `NullParameters` indicating that the equation does not have any parameters

### Subtypes

The `EquationProblem` type has various subtypes for the different equations types, that are defined e.g. via

```julia
const ODEProblem = EquationProblem{ODE}
```

and provide convenience constructors to construct an equation and the corresponding problem in one step, e.g.,

```julia
ODEProblem(v, tspan, tstep, ics::NamedTuple; kwargs...)
ODEProblem(v, tspan, tstep, q₀::StateVariable; kwargs...)
```

All problem subtypes take the following keyword arguments:

  * `invariants = NullInvariants()`
  * `parameters = NullParameters()`
  * `periodicity = NullPeriodicity()`

If not set to their corresponding Null types, the user needs to pass a `NamedTuple` whose values are

  * functions for invariants,
  * arbitrary data structures for parameters,
  * the same data structure as the solution for periodicity.

The latter should be zero everywhere, except for those components, that are periodic, i.e., whose value are supposed to stay within a range `(0, max)`. Support for ranges starting with other values than zero is currently missing but can be added if demand arises.
