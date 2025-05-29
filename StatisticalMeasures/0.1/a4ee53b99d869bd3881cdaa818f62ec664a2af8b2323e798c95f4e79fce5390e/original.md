```
MatthewsCorrelation()
```

Return a callable measure for computing the Matthew's correlation. Aliases: `matthews_correlation`, `mcc`.

```
MatthewsCorrelation()(ŷ, y)
```

Evaluate `MatthewsCorrelation()` on predictions `ŷ`, given ground truth observations `y`. See the [Wikipedia *Matthew's Correlation* page](https://en.wikipedia.org/wiki/Matthews_correlation_coefficient). Can also be called on confusion matrices.  See [`ConfusionMatrix`](@ref).

This metric is invariant to class reordering.

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). 

See also [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref).

Core algorithm: [`Functions.matthews_correlation`](@ref)

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = Matthew's correlation
```
