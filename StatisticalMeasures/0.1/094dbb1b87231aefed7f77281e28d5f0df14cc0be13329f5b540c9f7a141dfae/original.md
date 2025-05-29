```
LogCoshLoss()
```

Return a callable measure for computing the log cosh loss. Aliases: `log_cosh`, `log_cosh_loss`.

```
LogCoshLoss()(ŷ, y)
LogCoshLoss()(ŷ, y, weights)
LogCoshLoss()(ŷ, y, class_weights::AbstractDict)
LogCoshLoss()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `LogCoshLoss()` on predictions `ŷ`, given ground truth observations `y`. Return the mean of $\log(\cosh(ŷ_i-y_i))$ over all pairs of observations $(ŷ_i, y_i)$ in `(ŷ, y)`. More generally, pre-multiply the values averaged by the specified weights.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(LogCoshLoss(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`. 

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
human_name = log cosh loss
```
