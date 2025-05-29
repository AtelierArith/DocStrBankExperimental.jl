```
FScore(; beta=1.0, levels=nothing, rev=nothing, checks=true)
```

Return a callable measure for computing the $F_β$ score. Aliases: `f1score`.

```
m(ŷ, y)
```

Evaluate some measure `m` returned by the `FScore` constructor (e.g., `m = FScore()`) on predictions `ŷ`, given ground truth observations `y`. This is the one-parameter generalization, $F_β$, of the $F$-measure or balanced $F$-score. Choose `beta=β` in the range $[0,∞]$, using `beta > 1` to emphasize recall ([`TruePositiveRate`](@ref)) over precision ([`PositivePredictiveValue`](@ref)). When `beta = 1`, the score is the harmonic mean of precision and recall. See the [*F1 score* Wikipedia page](https://en.wikipedia.org/wiki/F-score) for details.

If ordering classes (levels) on the basis of the eltype of `y`, then the *second* level is the "positive" class. To reverse roles, specify `rev=true`.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

`FScore` mesaures can also be called on a confusion matrix.  See [`ConfusionMatrix`](@ref).

# Keyword options

  * `levels::Union{Vector,Nothing}=nothing`: if `nothing`, levels are inferred from  `ŷ` and `y` and, by default, ordered according to the element type of `y`.
  * `rev=false`: in the case of binary data, whether to reverse the `levels` (as inferred or specified); a `nothing` value is the same as `false`.

  * `checks=true`: when true, specified `levels` are checked to see they include all observed levels; set to `false` for speed.

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}` (binary classification where definition of "positive" class matters). 

See also [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref).

Core algorithm: [`Functions.fscore`](@ref) 

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
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = ``F_β`` score
```
