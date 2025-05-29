```
MulticlassFScore(; average=macro_avg, levels=nothing, more_options...)
```

Return a callable measure for computing the multi-class $F_β$ score. Aliases: `macro_f1score`, `micro_f1score`, `multiclass_f1score`.

```
m(ŷ, y)
m(ŷ, y, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `MulticlassFScore` constructor (e.g., `m = MulticlassFScore()`) on predictions `ŷ`, given ground truth observations `y`. 

This is an averaged one-versus-rest version of the binary [`FScore`](@ref). Or it can return a dictionary keyed on target class (or a vector); see `average` options below.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

You can also call `m` on confusion matrices. Construct confusion matrices using [`ConfusionMatrix`](@ref).

The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}` (binary classification where definition of "positive" class matters). 

# Keyword options

  * `beta=1.0`: parameter in the range $[0,∞]$, emphasizing recall over precision for `beta > 1`, except in the case `average=MicroAvg()`, when it has no effect.

  * `average=MacroAvg()`: one of: `NoAvg()`, `MacroAvg()`, `MicroAvg()` (names owned and exported by StatisticalMeasuresBase.jl.) See J. Opitz and S. Burst [(2019)](https://arxiv.org/abs/1911.03347). "Macro F1 and Macro F1", *arXiv*.

  * `return_type=LittleDict`: type of returned measurement for `average=NoAvg()` case; if `LittleDict`, then keyed on levels of the target; can also be `Vector`

  * `levels::Union{Vector,Nothing}=nothing`: if `nothing`, levels are inferred from  `ŷ` and `y` and, by default, ordered according to the element type of `y`.
  * `rev=false`: in the case of binary data, whether to reverse the `levels` (as inferred or specified); a `nothing` value is the same as `false`.

  * `perm=nothing`: in the general case, a permutation representing a re-ordering of `levels` (as inferred or specified); e.g., `perm = [1,3,2]` for data with three classes.

  * `checks=true`: when true, specified `levels` are checked to see they include all observed levels; set to `false` for speed.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

See also [`FScore`](@ref), [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref).

Core algorithm: [`Functions.multiclass_fscore`](@ref)

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = false
supports_class_weights = true
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = multi-class ``F_β`` score
```
