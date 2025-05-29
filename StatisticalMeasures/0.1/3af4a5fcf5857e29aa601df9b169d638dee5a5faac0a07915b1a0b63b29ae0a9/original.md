```
SphericalScore()
```

Return a callable measure for computing the spherical score. Aliases: `spherical_score`.

```
SphericalScore()(ŷ, y)
SphericalScore()(ŷ, y, weights)
SphericalScore()(ŷ, y, class_weights::AbstractDict)
SphericalScore()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `SphericalScore()` on predictions `ŷ`, given ground truth observations `y`. The score is a mean of observational scores. More generally, observational scores are pre-multiplied by the specified weights before averaging. See below for the form that probabilistic predictions `ŷ` should take.

Convention as in Gneiting and Raftery [(2007)](https://doi.org/10.1198/016214506000001437), "StrictlyProper Scoring Rules, Prediction, and Estimation": If `y` takes on a finite number of classes `C` and `p(y)` is the predicted probability for a single observation `y`, then the corresponding score for that example is given by

$p(y)^α / \left(\sum_{η ∈ C} p(η)^α\right)^{1-α} - 1$

where `α` is the measure parameter `alpha`.

In the case the predictions `ŷ` are continuous probability distributions, such as `Distributions.Normal`, replace the above sum with an integral, and interpret `p` as the probablity density function. In case of discrete distributions over the integers, such as `Distributions.Poisson`, sum over all integers instead of `C`.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(SphericalScore(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Missing,T}` where `T` is `Continuous` or `Count` (for respectively continuous or discrete Distribution.jl objects in `ŷ`) or  `OrderedFactor` or `Multiclass` (for `UnivariateFinite` distributions in `ŷ`). 

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
human_name = spherical score
```
