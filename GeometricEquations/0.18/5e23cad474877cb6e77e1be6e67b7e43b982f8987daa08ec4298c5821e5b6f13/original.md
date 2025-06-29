EnsembleProblem: stores a GeometricEquation together with multiple sets of initial conditions and/or parameters, a time span for integration and a time step size.

An `EnsembleProblem` is initialized by providing a `GeometricEquation`, an integration time span (typically a tuple with two values, start and end time, respectively), a timestep, and one of the three following options:

  * a vector of initial conditions and a vector of parameter sets, with both vectors having the same length,
  * a vector of initial conditions and a single set of parameters,
  * a single initial condition and a vector of parameter sets.

Each initial condition is a `NamedTuple` that contains one field for each state variable. Each parameter set is either a `NamedTuple` containing the equation's parameters or `NullParameters` indicating that the equation does not have any parameters.

The different constructors then generate two vectors, one for the initial conditions and one for the parameters, where each pair of the corresponding entries defines one problem. In the first case, the respective constructor just checks if both vectors are of the same size. In the second case, the respective constructor creates a parameter vector, where each entry holds the same parameter set. In the third case, the respective constructor creates an initial condition vector, where each entry holds the same initial conditions. One may be inclined to think that the first and second constructor lead to a waste of memory, but in reality the respective vectors only hold references to the same initial conditons or parameters. Thus the data is not actually duplicated.

Each pair of initial conditions and parameters is referred to as sample. The methods

```
length(::EnsembleProblem)
nsamples(::EnsembleProblem)
```

return the number of samples in a `EnsembleProblem`. A single initial condition or parameter set can be retrieved by the methods

```
initial_condition(::EnsembleProblem, i)
parameter(::EnsembleProblem, i)
```

where `i` is the index of the sample. Typically, however, e.g. when integrating all samples of an `EnsembleProblem` with GeometricIntegrators, it is more convenient to retrieve the corresponding `GeometricProblem` via the method

```
problem(::EnsembleProblem, i)
```

The `EnsembleProblem` also allows to iterate over all samples, e.g.

```
for problem in ensemble
    # ...
    # integrate problem
    # ...
end
```

where `ensemble` is an `EnsembleProblem` and `problem` is the corresponding `GeometricProblem`.

### Parameters

  * `ST <: GeometricEquation`: super type, used for dispatch
  * `DT <: Number`: data type
  * `TT <: Real`: time step type
  * `AT <: AbstractArray{DT}`: array type of state variable
  * `equType <: GeometricEquation`: equation type
  * `functionsType <: NamedTuple`: types of all function methods
  * `solutionsType <: NamedTuple`: types of all solution methods
  * `icsType <: AbstractVector{<:NamedTuple}`: types of all initial conditions
  * `parType <: AbstractVector{<:OptionalParameters}`: parameters type

### Fields

  * `equation`: reference to the parent equation object holding the vector fields, etc.
  * `functions`: methods for all vector fields, etc., that define the problem
  * `solutions`: methods for all solutions, etc., if defined
  * `tspan`: time span for problem `(t₀,t₁)`
  * `tstep`: time step to be used in simulation
  * `ics`: vector of `NamedTuple` containing the initial conditions, each `NamedTuple` must contain one field for each state variable
  * `parameters`: vector of either `NamedTuple` containing the equation's parameters or `NullParameters` indicating that the equation does not have any parameters

### Constructors

The `EnsembleProblem` provides the following constructors:

```
EnsembleProblem(equ, tspan, tstep, ics::AbstractVector{<:NamedTuple}, parameters::AbstractVector{<:OptionalParameters})
EnsembleProblem(equ, tspan, tstep, ics::AbstractVector{<:NamedTuple}, parameters::OptionalParameters=NullParameters())
EnsembleProblem(equ, tspan, tstep, ics::NamedTuple, parameters::AbstractVector{<:OptionalParameters})
EnsembleProblem(equ, tspan, tstep, ics, ::Nothing) = 
    EnsembleProblem(equ, tspan, tstep, ics, NullParameters())
EnsembleProblem(equ, tspan, tstep, ics; parameters = NullParameters()) = 
    EnsembleProblem(equ, tspan, tstep, ics, parameters)
```

  * `equ` is a subtype of `GeometricEquation`
  * `tspan` is a tuple `(t₀,t₁)` of the integration time span with `t₀` the start time and `t₁` the end time
  * `tstep` is the time step, typically a value of some `AbstractFloat` subtype
  * `ics` are the initial conditions, either a single set or a vector of multiple sets
  * `parameters` are the static parameters of the problem, either a single set or a vector of multiple sets
