```
MeanAbsoluteProportionalError(; tol=eps())
```

Return a callable measure for computing the mean absolute proportional error. Aliases: `mape`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `MeanAbsoluteProportionalError` constructor (e.g., `m = MeanAbsoluteProportionalError()`) on predictions `ŷ`, given ground truth observations `y`. Specifically, return the mean of $|ŷ_i-y_i| \over |y_i|$ over all pairs of observations $(ŷ_i, y_i)$ in `(ŷ, y)`. More generally, pre-multiply the values averaged by the specified weights. Terms for which $|y_i|$<`tol` are dropped in the summation, but corresponding weights (or counts) still contribute to the mean normalization factor.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(m, ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`. 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = mean absolute proportional error
```
