```
global_continuation(gca::GlobalContinuationAlgorithm, prange, pidx, ics; kwargs...)
global_continuation(gca::GlobalContinuationAlgorithm, pcurve, ics; kwargs...)
```

Find and continue attractors (or representations of attractors) and the fractions of their basins of attraction across a parameter range `pcurve` by sampling given initial conditions `ics` according to algorithm `gca`.

Return:

1. `fractions_cont::Vector{Dict{Int, Float64}}`. The fractions of basins of attraction. `fractions_cont[i]` is a dictionary mapping attractor IDs to their basin fraction at the `i`-th parameter combination.

      * This output is different if you are using [`StabilityMeasuresAccumulator`](@ref)  in combination with [`AttractorSeedContinueMatch`](@ref). See the docstring  of [`StabilityMeasuresAccumulator`](@ref) for more details.
2. `attractors_cont::Vector{Dict{Int, <:Any}}`. The continued attractors. `attractors_cont[i]` is a dictionary mapping attractor ID to the attractor set at the `i`-th parameter combination.

See the function [`continuation_series`](@ref) if you wish to transform the output to an alternative format.

## Keyword arguments

  * `show_progress = true`: display a progress bar of the computation.
  * `samples_per_parameter = 100`: amount of initial conditions sampled at each parameter combination from `ics` if `ics` is a function instead of set initial conditions.

## Description

`global_continuation` is the central function of the framework for global stability analysis illustrated in [Datseris2023](@cite).

The global continuation algorithm typically references an [`AttractorMapper`](@ref) which is used to find the attractors and basins of a dynamical system. Additional arguments that control how to continue/track/match attractors across a parameter range are given when creating `gca`.

The basin fractions and the attractors (or some representation of them) are continued across the parameter range `prange`, for the parameter of the system with index `pidx` (any index valid in `DynamicalSystems.set_parameter!` can be used). In contrast to traditional continuation (see online Tutorial for a comparison), global continuation can be performed over arbitrary user-defined curves in parameter space. The second call signature with `pcurve` allows for this possibility. In this case `pcurve` is a vector of iterables, where each itereable maps parameter indices to parameter values. These iterables can be dictionaries, named tuples, `Vector{Pair}`, etc., and the sequence of the iterables defines a curve in parameter space. In fact, the version with `prange, pidx` simply defines `pcurve = [[pidx => p] for p in prange]` and calls the second method.

`ics` are the initial conditions to use when globally sampling the state space. Like in [`basins_fractions`](@ref) it can be either a set vector of initial conditions, or a 0-argument function that generates random initial conditions.

Possible subtypes of `GlobalContinuationAlgorithm` are:

  * [`AttractorSeedContinueMatch`](@ref)
  * [`FeaturizeGroupAcrossParameter`](@ref)
