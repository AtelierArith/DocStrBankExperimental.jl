```
TrueNegative(; levels=nothing, rev=nothing, checks=true)
```

Return a callable measure for computing the true negative count. Aliases: `true_negative`, `truenegative`.

```
m(ŷ, y)
```

Evaluate some measure `m` returned by the `TrueNegative` constructor (e.g., `m = TrueNegative()`) on predictions `ŷ`, given ground truth observations `y`. When ordering classes (levels) on the basis of the eltype of `y`, the *second* level is the "positive" class. To reverse roles, specify `rev=true`.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

`m` can also be called on a confusion matrix. See [`ConfusionMatrix`](@ref).

# Keyword options

  * `levels::Union{Vector,Nothing}=nothing`: if `nothing`, levels are inferred from  `ŷ` and `y` and, by default, ordered according to the element type of `y`.
  * `rev=false`: in the case of binary data, whether to reverse the `levels` (as inferred or specified); a `nothing` value is the same as `false`.

  * `checks=true`: when true, specified `levels` are checked to see they include all observed levels; set to `false` for speed.

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}` (binary classification where definition of "positive" class matters). 

See also [`MulticlassTrueNegative`](@ref), [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref).

Core algorithm: [`Functions.true_negative`](@ref)

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.OrderedFactor{2}}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = true negative count
```
