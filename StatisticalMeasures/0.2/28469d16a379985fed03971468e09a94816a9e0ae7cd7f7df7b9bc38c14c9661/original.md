```
LogScore(; tol=eps())
```

Return a callable measure for computing the log score. Aliases: `log_score`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate some measure `m` returned by the `LogScore` constructor (e.g., `m = LogScore()`) on predictions `ŷ`, given ground truth observations `y`. The score is a mean of observational scores. More generally, observational scores are pre-multiplied by the specified weights before averaging. See below for the form that probabilistic predictions `ŷ` should take. Raw probabilities are clamped away from `0` and `1`. Specifically, if `p` is the probability mass/density function evaluated at given observed ground truth observation `η`, then the score for that example is defined as

```
log(clamp(p(η), tol, 1 - tol).
```

For example, for a binary target with "yes"/"no" labels, if the probabilistic prediction scores 0.8 for a "yes", then for a corresponding ground truth observation of "no", that example's contribution to the score is `log(0.2)`.

The predictions `ŷ` should be a vector of `UnivariateFinite` distributions from CategoricalDistritutions.jl, in the case of `Finite` target `y` (a `CategoricalVector`) and should otherwise be a supported `Distributions.UnivariateDistribution` such as `Normal` or `Poisson`.

See also [`LogLoss`](@ref), which differs only in sign.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(m, ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Missing,T}` where `T` is `Continuous` or `Count` (for respectively continuous or discrete Distribution.jl objects in `ŷ`) or  `OrderedFactor` or `Multiclass` (for `UnivariateFinite` distributions in `ŷ`). 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Distribution()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = log score
```
