```
Accuracy()
```

Return a callable measure for computing the accuracy. Aliases: `accuracy`.

```
Accuracy()(ŷ, y)
Accuracy()(ŷ, y, weights)
Accuracy()(ŷ, y, class_weights::AbstractDict)
Accuracy()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `Accuracy()` on predictions `ŷ`, given ground truth observations `y`. That is, compute the proportion of predictions `ŷᵢ` that agree with the corresponding ground truth `yᵢ`. More generally, average the specified weights over all correctly predicted observations.  Can also be called on a confusion matrix. See [`ConfusionMatrix`](@ref).

This metric is invariant to class reordering.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(Accuracy(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). 

See also [`ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref). 

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
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = accuracy
```
