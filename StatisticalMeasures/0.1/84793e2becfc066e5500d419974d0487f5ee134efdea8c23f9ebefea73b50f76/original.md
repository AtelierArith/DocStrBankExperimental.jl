```
MulticlassTruePositive(; levels=nothing, more_options...)
```

Return a callable measure for computing the multi-class true positive count. Aliases: `multiclass_true_positive`, `multiclass_truepositive`.

```
m(ŷ, y)
```

Evaluate some measure `m` returned by the `MulticlassTruePositive` constructor (e.g., `m = MulticlassTruePositive()`) on predictions `ŷ`, given ground truth observations `y`. 

This is a one-versus-rest version of the binary measure [`TruePositive`](@ref), returning a dictionary keyed on target class (level), or a vector (see options below), instead of a single number, even on binary data.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

`m` can also be called on a confusion matrix.  Construct confusion matrices using [`ConfusionMatrix`](@ref).

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{OrderedFactor{2},Missing}` (binary classification where definition of "positive" class matters). 

# Keyword options

  * `return_type=LittleDict`: type of returned measurement for `average=NoAvg()` case; if `LittleDict`, then keyed on levels of the target; can also be `Vector`

  * `levels::Union{Vector,Nothing}=nothing`: if `nothing`, levels are inferred from  `ŷ` and `y` and, by default, ordered according to the element type of `y`.
  * `rev=false`: in the case of binary data, whether to reverse the `levels` (as inferred or specified); a `nothing` value is the same as `false`.

  * `perm=nothing`: in the general case, a permutation representing a re-ordering of `levels` (as inferred or specified); e.g., `perm = [1,3,2]` for data with three classes.

  * `checks=true`: when true, specified `levels` are checked to see they include all observed levels; set to `false` for speed.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

See also [`TruePositive`](@ref), [`StatisticalMeasures.ConfusionMatrices.ConfusionMatrix`](@ref) and [`ConfusionMatrix`](@ref).

Core algorithm: [`Functions.multiclass_true_positive`](@ref)

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
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = multi-class true positive count
```
