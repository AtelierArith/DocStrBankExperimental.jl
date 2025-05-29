```
stability_measures_along_continuation(
    ds::DynamicalSystem, attractors_cont, pcurve, ics;
    kw...
)
```

Perform a global continuation of all stability measures estimated by [`StabilityMeasuresAccumulator`](@ref) using the found attractors of a previous call to [`global_continuation`](@ref) using the `ds`.

This method is special because it always creates an [`AttractorsViaProximity`](@ref) mapper for the attractors at a given point along the global continuation, and then estimates the stability measures using [`StabilityMeasuresAccumulator`](@ref) and the proximity mapper. Realistically you only want to use this method if you are interested in measures related to the convergence time, which is defined more rirogously and is estimated more accurately for a proximity mapper.

## Keyword arguments

Keywords `ε, finite_time, weighting_distribution` are allowed to be `Vector`s with the same length as `pcurve` for providing different values for different continuation steps.

  * `ε = nothing`: given to [`AttractorsViaProximity`](@ref).
  * `proximity_mapper_options = NamedTuple()`: extra keywords for `AttractorsViaProximity`.
  * `metric, finite_time, weighting_distribution`: given to [`StabilityMeasuresAccumulator`](@ref).
  * `samples_per_parameter = 1000`: how many samples to use when estimating stability measures via [`StabilityMeasuresAccumulator`](@ref). Ignored when `ics` is not a function.
