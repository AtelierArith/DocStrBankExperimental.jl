```
RootMeanSquaredProportionalError(; tol=eps())
```

Return a callable measure for computing the root mean squared proportional error. Aliases: `rmsp`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `RootMeanSquaredProportionalError` constructor (e.g., `m = RootMeanSquaredProportionalError()`) on predictions `ŷ`, given ground truth observations `y`. Specifically, compute the mean of `((ŷᵢ-yᵢ)/yᵢ)^2}` over all pairs of observations `(ŷᵢ, yᵢ)` in `(ŷ, y)`, and return the square root of the result. More generally, pre-multiply the values averaged by the specified weights. Terms for which `abs(yᵢ) < tol` are dropped in the summation, but counts still contribute to the mean normalization factor.

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
external_aggregation_mode = StatisticalMeasuresBase.RootMean{Int64}(2)
human_name = root mean squared proportional error
```
