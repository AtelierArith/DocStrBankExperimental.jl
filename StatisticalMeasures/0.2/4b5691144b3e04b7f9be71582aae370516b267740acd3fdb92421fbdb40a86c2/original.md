```
BalancedAccuracy(; adjusted=false)
```

Return a callable measure for computing the balanced accuracy. Aliases: `balanced_accuracy`, `bacc`, `bac`, `probability_of_correct_classification`.

```
m(ŷ, y)
m(ŷ, y, weights)
```

Evaluate some measure `m` returned by the `BalancedAccuracy` constructor (e.g., `m = BalancedAccuracy()`) on predictions `ŷ`, given ground truth observations `y`. This is a variation of [`Accuracy`](@ref) compensating for class imbalance. See [https://en.wikipedia.org/wiki/Precision*and*recall#Imbalanced_data](https://en.wikipedia.org/wiki/Precision_and_recall#Imbalanced_data).

Setting `adjusted=true` rescales the score in the way prescribed in [L. Mosley (2013)](https://lib.dr.iastate.edu/etd/13537/): A balanced approach to the multi-class imbalance problem. PhD thesis, Iowa State University. In the binary case, the adjusted balanced accuracy is also known as *Youden’s J statistic*, or *informedness*.

Can also be called on a confusion matrix. See [`ConfusionMatrix`](@ref).

This metric is invariant to class reordering.

Any iterator with a `length` generating `Real` elements can be used for `weights`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = balanced accuracy
```
