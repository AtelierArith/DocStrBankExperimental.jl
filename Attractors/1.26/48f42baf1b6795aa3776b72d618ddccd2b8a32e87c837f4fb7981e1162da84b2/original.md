```
StabilityMeasuresAccumulator(mapper::AttractorMapper; kwargs...)
```

A special data structure that allows mapping initial conditions to attractors while *at the same time* calculating many stability measures in the most efficient way possible. `mapper` is any instance of an [`AttractorMapper`](@ref) that implements the `id = mapper(u0)` syntax. This functionality was developed as part of [Morr2025](@cite). If you use it, cite this paper along with the Attractors.jl publication [Datseris2023](@cite).

`StabilityMeasuresAccumulator` can be used as any `AttractorMapper` with library functions such as [`basins_fractions`](@ref). After mapping all initial conditions to attractors, the [`finalize_accumulator`](@ref) function should be called which will return a dictionary of all stability measures estimated by the accumulator. Each dictionary maps the measure description (`String`) to a dictionary mapping attractor IDs to the measure value. Calling `reset_mapper!(accumulator)` cleans up all accumulated measures.

**Using with [`global_continuation`](@ref)**: Since `StabilityMeasuresAccumulator` is formally an `AttractorMapper`, it can be used with [`global_continuation`](@ref). Simply give it as a `mapper` input to [`AttractorSeedContinueMatch`](@ref) and then call `global_continuation` as normal. The only difference now is that `global_continuation` will not return just one measure of nonlocal stability (the basin fraction). Rather, now the first return argument of `global_continuation` will be a `measures_cont`, a dictionary mapping nonlocal stability measures (strings) to vectors of dictionaries. Each vector of dictionaries is similar to `fractions_cont` of the typical [`global_continuation`](@ref): each dictionary maps attractor ID to the corresponding nonlocal stability measure.

Use [`stability_measures_along_continuation`](@ref) for continuation of stability  measures computed on the basis of an `AttractorsViaProximity` mapper from already found attractors. This is useful to do for measures related to the convergence time, which is defined more rirogously and is estimated more accurately for a proximity mapper.

## Keyword arguments

  * `finite_time = 1.0`: Finite time horizon considered for the computation of the `finite_time_basin_stability`. Initial coditions with a convergence time larger than `finite_time` are not considered to be in the respective finite time basin. Convergence time is determined by the `mapper`.
  * `weighting_distribution::Distribution`: Distribution of uncertain initial conditions used for example in the computation of `basin_stability`. By default it is a uniform distribution everywhere in the state space.

## Description

`StabilityMeasuresAccumulator` efficiently uses a single `id = mapper(u0)` call to accumulate information for many differnt stability measures corresponding to each attractor of the dynamical system. It accumulates all these different measures when different initial conditions are mapped through it. After enough `u0`s have been given to the accumulator, they can be finalized (comput maxima or averages) using `finalize!(accumulator)`.

The following stability measures are estimated for each attractor (and the returned dictionary maps strings with the names of the measures to the dictionaries containing the measure values for each attractor):

### Local (fixed point) stability measures

These measures apply only to fixed point attractors. Their value is `NaN` if an attractor is not a fixed point (`length(A) > 1`). If an unstable fixed point attractor is recorded (due to an initial condition starting there for example), a value `Inf` is assigned to all measures. Currently linear measures for discrete time systems are not computed.

  * `characteristic_return_time`: The reciprocal of the largest real part of the eigenvalues of the Jacobian matrix at the fixed point.
  * `reactivity`: The largest growth rate of the linearized system at the fixed point. See also [Krakovska2024ResilienceDynamicalSystems](@cite).
  * `maximal_amplification`: The maximal (with respect to disturbances) amplification of the linearized system at the attractor over all time.
  * `maximal_amplification_time`: The time at which the maximal amplification occurs.

### Nonlocal stability measures

These nonlocal stability measures are accumulated while initial conditions are mapped to attractors. Afterwards they are averaged according to the probability density `weighting_distribution` when calling `finalize_accumulator!`. The word "distance" here refers to the distance established by the `metric` keyword.

  * `mean_convergence_time`: The convergence time is determined by the `mapper` using [`convergence_time`](@ref). The mean is computed with respect to the `weighting_distribution`.
  * `maximal_convergence_time`: The maximal convergence time of initial conditions to the attractor. Only initial conditions with non-zero probability under `weighting_distribution` are considered.
  * `median_convergence_time`: The median convergence time of initial conditions. Only initial conditions with non-zero probability under `weighting_distribution` are considered.
  * `mean_convergence_pace`: The mean convergence pace of initial conditions to the attractor. Similar to the mean convergence time, except that each convergence time is divided by the distance of the respective initial condition to the attractor.
  * `maximal_convergence_pace`: The maximal convergence pace of initial conditions to the attractor. Only initial conditions with non-zero probability under `weighting_distribution` are considered.
  * `median_convergence_pace`: The median convergence pace of initial conditions. Only initial conditions with non-zero probability under `weighting_distribution` are considered.
  * `minimal_critical_shock_magnitude`: The minimal distance of the attractor to the closest non-zero probability point (under `weighting_distribution`) in a basin of attraction of a different attractor. If only a single attractor exists, the value `Inf` is assigned.
  * `maximal_noncritical_shock_magnitude`: The distance of the attractor to the furthest non-zero probability point (under `weighting_distribution`) of its own basin of attraction. If only a single attractor exists, the value `Inf` is assigned.
  * `mean_noncritical_shock_magnitude`: same as above but the mean instead of maximum distance.
  * `basin_fraction`: The fraction of initial conditions that converge to the attractor.
  * `basin_stability`: The fraction of initial conditions that converge to the attractor, weighted by `weighting_distribution`. For the default value of `weighting_distribution` this is identical to `basin_fraction`.
  * `finite_time_basin_stability`: The fraction of initial conditions that converge to the attractor within the time horizon `finite_time`, weighted by `weighting_distribution`.
