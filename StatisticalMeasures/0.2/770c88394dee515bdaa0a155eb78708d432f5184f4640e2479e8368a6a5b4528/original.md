```
AreaUnderCurve()
```

Return a callable measure for computing the area under the receiver operator characteritic. Aliases: `auc`, `area_under_curve`.

```
AreaUnderCurve()(ŷ, y)
```

Evaluate `AreaUnderCurve()` on predictions `ŷ`, given ground truth observations `y`. See the [*Recevier operator chararacteristic*](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) (ROC) Wikipedia article for a definition. It is expected that `ŷ` be a vector of distributions over the binary set of unique elements of `y`; specifically, `ŷ` should have eltype `<:UnivariateFinite` from the CategoricalDistributions.jl package.

Implementation is based on the Mann-Whitney U statistic.  See the [*Whitney U test*](https://en.wikipedia.org/wiki/Mann%E2%80%93Whitney_U_test#Area_under_curve_(AUC)_statistic_for_ROC_curves) Wikipedia page for details. 

Core implementation: [`Functions.auc`](@ref).

This metric is invariant to class reordering.

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``ScientificTypesBase.Binary`. 

See also [`roc_curve`](@ref). 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Distribution()
observation_scitype = ScientificTypesBase.Binary
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = area under the receiver operator characteritic
```
