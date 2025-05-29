```
MultitargetRootMeanSquaredError(; atomic_weights=nothing)
```

Return a callable measure for computing the multitarget root mean squared error. Aliases: `multitarget_rms`, `multitarget_rmse`, `multitarget_root_mean_squared_error`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `MultitargetRootMeanSquaredError` constructor (e.g., `m = MultitargetRootMeanSquaredError()`) on predictions `ŷ`, given ground truth observations `y`. Specifically, compute the multi-target version of [`RootMeanSquaredError`](@ref). Some kinds of tabular input are supported.

In array arguments the last dimension is understood to be the observation dimension. The `atomic_weights` are weights for each component of the multi-target. Unless equal to `nothing` (uniform weights) the length of `atomic_weights` will generally match the number of columns of `y`, if `y` is a table, or the number of rows of `y`, if `y` is a matrix. 

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(m, ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``AbstractArray{<:Union{Missing,Infinite}}`. Alternatively, `y` and `ŷ` can be some types of table, provided elements have the approprate scitype. 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Point()
observation_scitype = AbstractArray{<:Union{Missing, ScientificTypesBase.Infinite}}
can_consume_tables = true
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.RootMean{Int64}(2)
human_name = multitarget root mean squared error
```
