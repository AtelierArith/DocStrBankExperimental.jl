```
ConfusionMatrix(; levels=nothing, rev=false, perm=nothing, checks=true)
```

Return a callable measure for computing the confusion matrix. Aliases: `confmat`, `confusion_matrix`.

```
m(ŷ, y)
```

Evaluate some measure `m` returned by the `ConfusionMatrix` constructor (e.g., `m = ConfusionMatrix()`) on predictions `ŷ`, given ground truth observations `y`. See the [*Confusion matrix* wikipedia article](https://en.wikipedia.org/wiki/Confusion_matrix).

Elements of a confusion matrix can always be accessed by level - see the example below. To flag the confusion matrix as ordered, and hence index-accessible, do one of the following:

  * Supply ordered `CategoricalArray` inputs `ŷ` and `y`
  * Explicitly specify `levels` or one of `rev`, `perm`

Note that `==` for two confusion matrices is stricter when both are ordered.

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Finite,Missing}` (multiclass classification). 

# Keyword options

  * `levels::Union{Vector,Nothing}=nothing`: if `nothing`, levels are inferred from  `ŷ` and `y` and, by default, ordered according to the element type of `y`.
  * `rev=false`: in the case of binary data, whether to reverse the `levels` (as inferred or specified); a `nothing` value is the same as `false`.

  * `perm=nothing`: in the general case, a permutation representing a re-ordering of `levels` (as inferred or specified); e.g., `perm = [1,3,2]` for data with three classes.

  * `checks=true`: when true, specified `levels` are checked to see they include all observed levels; set to `false` for speed.

Method is optimized for `CategoricalArray` inputs with `levels` inferred. In that case `levels` will be the complete internal class pool, and not just the observed levels.

For more on the type of object returned and its interface, see [`ConfusionMatrices.ConfusionMatrix`](@ref).

# Example

```julia

using StatisticalMeasures

y = ["a", "b", "a", "a", "b", "a", "a", "b", "b", "a"]
ŷ = ["b", "a", "a", "b", "a", "b", "b", "b", "a", "a"]

julia> cm = ConfusionMatrix()(ŷ, y)  # or `confmat((ŷ, y)`.

              ┌───────────────────────────┐
              │       Ground Truth        │
┌─────────────┼─────────────┬─────────────┤
│  Predicted  │      a      │      b      │
├─────────────┼─────────────┼─────────────┤
│      a      │      2      │      3      │
├─────────────┼─────────────┼─────────────┤
│      b      │      4      │      1      │
└─────────────┴─────────────┴─────────────┘

julia> cm("a", "b")
3
```

Core algorithm:  [`ConfusionMatrices.confmat`](@ref).

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Unoriented()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = confusion matrix
```
