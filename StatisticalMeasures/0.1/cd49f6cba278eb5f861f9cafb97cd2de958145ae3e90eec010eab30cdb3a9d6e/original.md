```
MultitargetMisclassificationRate()
```

Return a callable measure for computing the multitarget misclassification rate. Aliases: `multitarget_misclassification_rate`, `multitarget_mcr`.

```
MultitargetMisclassificationRate()(ŷ, y)
MultitargetMisclassificationRate()(ŷ, y, weights)
MultitargetMisclassificationRate()(ŷ, y, class_weights::AbstractDict)
MultitargetMisclassificationRate()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `MultitargetMisclassificationRate()` on predictions `ŷ`, given ground truth observations `y`. Specifically, compute the multi-target version of [`MisclassificationRate`](@ref). Some kinds of tabular input are supported.

In array arguments the last dimension is understood to be the observation dimension. The `atomic_weights` are weights for each component of the multi-target. Unless equal to `nothing` (uniform weights) the length of `atomic_weights` will generally match the number of columns of `y`, if `y` is a table, or the number of rows of `y`, if `y` is a matrix. 

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(MultitargetMisclassificationRate(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). Alternatively, `y` and `ŷ` can be some types of table, provided elements have the approprate scitype. 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = AbstractArray{<:Union{Missing, ScientificTypesBase.Finite}}
can_consume_tables = true
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = multitarget misclassification rate
```
