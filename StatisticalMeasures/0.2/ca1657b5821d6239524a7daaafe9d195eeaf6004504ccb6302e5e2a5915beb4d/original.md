```
LPSumLoss(; p=2)
```

Return a callable measure for computing the $L^p$ sum loss. Aliases: `l1_sum`, `l2_sum`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `LPSumLoss` constructor (e.g., `m = LPSumLoss()`) on predictions `ŷ`, given ground truth observations `y`. Specifically, compute the (weighted) sum of $|ŷ_i - yᵢ|^p$ over all pairs of observations $(ŷ_i, yᵢ)$ in `(ŷ, y)`. For the weighted *mean* use [`LPLoss`](@ref) instead.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(m, ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`. 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = ``L^p`` sum loss
```
