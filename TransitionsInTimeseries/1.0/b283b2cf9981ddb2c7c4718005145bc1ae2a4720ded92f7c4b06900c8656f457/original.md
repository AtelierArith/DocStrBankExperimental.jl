```
SurrogatesSignificance <: Significance
SurrogatesSignificance(; kwargs...)
```

A configuration struct for significance testing [`significant_transitions`](@ref) using timeseries surrogates.

## Keyword arguments

  * `surromethod = RandomFourier()`: method to generate surrogates
  * `n = 1000`: how many surrogates to generate
  * `rng = Random.default_rng()`: random number generator for the surrogates
  * `p = 0.05`: threshold for significance of the p-value
  * `tail = :both`: tail type used, see below

## Description

When used with [`ChangesResults`](@ref), significance is estimated as follows: `n` surrogates from the input timeseries are generated using `surromethod`, which is any `Surrogate` subtype provided by [TimeseriesSurrogates.jl](https://juliadynamics.github.io/TimeseriesSurrogates.jl/dev/api/). For each surrogate, the indicator and then change metric timeseries is extracted. The values of the surrogate change metrics form a distribution of values (one at each time point). The value of the original change metric is compared to that of the surrogate distribution and a p-value is extracted according to the specified `tail`. The p-value is compared with `p` to claim significance. After using `SurrogatesSignificance`, you may access the full p-values before thresholding in the field `.pvalues` (to e.g., threshold with different `p`).

The p-value is simply the proportion of surrogate change metric values that exceed (for `tail = :right`) or subseed (`tail = :left`) the original change metric at each given time point. Use `tail = :left` if the surrogate data are expected to have higher change metric values. This is the case for statistics that quantify entropy. For statistics that quantify autocorrelation, use `tail = :right` instead. For anything else, use the default `tail = :both`. An iterable of `tail` values can also be given, in which case a specific `tail` is used for each change metric in [`ChangesResults`](@ref).

Note that the raw p-values can be accessed in the field `.pvalues`, after calling the [`significant_transitions`](@ref) function with `SurrogatesSignificance`, in case you wish to obtain a different threshold of the p-values.
