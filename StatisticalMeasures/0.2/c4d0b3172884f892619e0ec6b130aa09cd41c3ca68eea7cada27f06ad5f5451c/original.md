```
MisclassificationRate()
```

Return a callable measure for computing the misclassification rate. Aliases: `misclassification_rate`, `mcr`.

```
MisclassificationRate()(ŷ, y)
MisclassificationRate()(ŷ, y, weights)
MisclassificationRate()(ŷ, y, class_weights::AbstractDict)
MisclassificationRate()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `MisclassificationRate()` on predictions `ŷ`, given ground truth observations `y`. That, is, return the proportion of predictions `ŷᵢ` that are different from the corresponding ground truth `yᵢ`. More generally, average the specified weights over incorrectly identified observations. Can also be called on a confusion matrix. See [`ConfusionMatrix`](@ref).

This metric is invariant to class reordering.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(MisclassificationRate(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). 

See also [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref). 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = misclassification rate
```
