```
RootMeanSquaredLogProportionalError(; offset=1)
```

Return a callable measure for computing the root mean squared log proportional error. Aliases: `rmslp1`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `RootMeanSquaredLogProportionalError` constructor (e.g., `m = RootMeanSquaredLogProportionalError()`) on predictions `ŷ`, given ground truth observations `y`. Specifically, compute the mean of $(\log(ŷ_i + δ) - \log(y_i + δ))^2$ over all pairs of observations $(ŷ_i, y_i)$ in `(ŷ, y)`, and return the square root. More generally, pre-multiply the values averaged by the specified weights. Here $δ$=`offset`, which is `1` by default. This is the same as [`RootMeanSquaredLogError`](@ref) but adds an offset.

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
human_name = root mean squared log proportional error
```
