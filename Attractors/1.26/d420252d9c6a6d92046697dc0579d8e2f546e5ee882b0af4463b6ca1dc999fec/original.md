```
basins_fractions(
    mapper::AttractorMapper,
    ics::Union{AbstractVector, Function};
    kwargs...
)
```

Approximate the state space fractions `fs` of the basins of attraction of a dynamical system by mapping initial conditions to attractors using `mapper` (which contains a reference to a [`DynamicalSystem`](@ref)). The fractions are simply the ratios of how many initial conditions ended up at each attractor.

Initial conditions to use are defined by `ics`. It can be:

  * an `AbstractVector` of initial conditions, in which case all are used. Typically this is a `StateSpaceSet`.
  * a 0-argument function `ics()` that spits out random initial conditions. Then `N` random initial conditions are chosen. See [`statespace_sampler`](@ref) to generate such functions.

## Return

The function will always return `fractions`, which is a dictionary whose keys are the labels given to each attractor (always integers enumerating the different attractors), and whose values are the respective basins fractions. The label `-1` is given to any initial condition where `mapper` could not match to an attractor (this depends on the `mapper` type).

If `ics` is a `StateSpaceSet` the function will also return `labels`, which is a *vector*, of equal length to `ics`, that contains the label each initial condition was mapped to.

See [`AttractorMapper`](@ref) for all possible `mapper` types, and use [`extract_attractors`](@ref) (after calling `basins_fractions`) to extract the stored attractors from the `mapper`. See also [`convergence_and_basins_fractions`](@ref).

## Keyword arguments

  * `N = 1000`: Number of random initial conditions to generate in case `ics` is a function.
  * `show_progress = true`: Display a progress bar of the process.
