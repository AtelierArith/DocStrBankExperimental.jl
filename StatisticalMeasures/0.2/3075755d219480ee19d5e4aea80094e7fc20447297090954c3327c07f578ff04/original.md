```
LogLoss(; tol=eps())
```

Return a callable measure for computing the log loss. Aliases: `log_loss`, `cross_entropy`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `LogLoss` constructor (e.g., `m = LogLoss()`) on predictions `ŷ`, given ground truth observations `y`. For details, see [`LogScore`](@ref), which differs only by a sign.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(m, ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Missing,T}` where `T` is `Continuous` or `Count` (for respectively continuous or discrete Distribution.jl objects in `ŷ`) or  `OrderedFactor` or `Multiclass` (for `UnivariateFinite` distributions in `ŷ`). 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Distribution()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = log loss
```
