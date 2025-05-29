```
Kappa()
```

Return a callable measure for computing the Cohen's κ. Aliases: `kappa`.

```
Kappa()(ŷ, y)
Kappa()(ŷ, y, weights)
```

Evaluate `Kappa()` on predictions `ŷ`, given ground truth observations `y`. For details, see the [Cohen's κ](https://en.wikipedia.org/wiki/Cohen%27s_kappa) Wikipedia article. Can also be called on confusion matrices. See [`ConfusionMatrix`](@ref).

This metric is invariant to class reordering.

Any iterator with a `length` generating `Real` elements can be used for `weights`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). 

See also [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref). 

Core algorithm: [`Functions.kappa`](@ref)

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
human_name = Cohen's κ
```
