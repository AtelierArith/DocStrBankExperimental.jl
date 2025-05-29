```
BrierLoss()
```

Return a callable measure for computing the brier loss. Aliases: `brier_loss`, `cross_entropy`, `quadratic_loss`.

```
BrierLoss()(ŷ, y)
BrierLoss()(ŷ, y, weights)
BrierLoss()(ŷ, y, class_weights::AbstractDict)
BrierLoss()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `BrierLoss()` on predictions `ŷ`, given ground truth observations `y`. For details, see [`BrierScore`](@ref), which differs only by a sign.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(BrierLoss(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Missing,T}` where `T` is `Continuous` or `Count` (for respectively continuous or discrete Distribution.jl objects in `ŷ`) or  `OrderedFactor` or `Multiclass` (for `UnivariateFinite` distributions in `ŷ`). 

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
human_name = brier loss
```
