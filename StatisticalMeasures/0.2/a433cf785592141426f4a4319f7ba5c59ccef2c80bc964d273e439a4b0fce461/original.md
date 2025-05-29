```
RootMeanSquaredLogError()
```

Return a callable measure for computing the root mean squared log error. Aliases: `rmsl`, `rmsle`, `root_mean_squared_log_error`.

```
RootMeanSquaredLogError()(ŷ, y)
RootMeanSquaredLogError()(ŷ, y, weights)
RootMeanSquaredLogError()(ŷ, y, class_weights::AbstractDict)
RootMeanSquaredLogError()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `RootMeanSquaredLogError()` on predictions `ŷ`, given ground truth observations `y`. Specifically, return the mean of $(\log(y)_i - \log(ŷ_i))^2$ over all pairs of observations $(ŷ_i, y_i)$ in `(ŷ, y)`, and return the square root of the result. More generally, pre-multiply the values averaged by the specified weights. To include an offset, use [`RootMeanSquaredLogProportionalError`](@ref) instead.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(RootMeanSquaredLogError(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`. 

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
external_aggregation_mode = StatisticalMeasuresBase.RootMean{Int64}(2)
human_name = root mean squared log error
```
