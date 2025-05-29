```
BrierScore()
```

Return a callable measure for computing the brier score. Aliases: `brier_score`, `quadratic_score`.

```
BrierScore()(ŷ, y)
BrierScore()(ŷ, y, weights)
BrierScore()(ŷ, y, class_weights::AbstractDict)
BrierScore()(ŷ, y, weights, class_weights::AbstractDict)
```

Evaluate `BrierScore()` on predictions `ŷ`, given ground truth observations `y`. The score is a mean of observational scores. More generally, observational scores are pre-multiplied by the specified weights before averaging. See below for the form that probabilistic predictions `ŷ` should take.

Convention as in Gneiting and Raftery [(2007)](https://doi.org/10.1198/016214506000001437), "StrictlyProper Scoring Rules, Prediction, and Estimation"

*Finite case.* If `p(η)` is the predicted probability for a *single* observation `η`, and `C` all possible classes, then the corresponding score for that example is given by

$2p(η) - \left(\sum_{c ∈ C} p(c)^2\right) - 1$

*Warning.* `BrierScore()` is a "score" in the sense that bigger is better (with `0` optimal, and all other values negative). In Brier's original 1950 paper, and many other places, it has the opposite sign, despite the name. Moreover, the present implementation does not treat the binary case as special, so that the score may differ in the binary case by a factor of two from usage elsewhere.

*Infinite case.* Replacing the sum above with an integral does *not* lead to the formula adopted here in the case of `Continuous` or `Count` target `y`. Rather the convention in the paper cited above is adopted, which means returning a score of

$2p(η) - ∫ p(t)^2 dt$

in the `Continuous` case (`p` the probablity density function) or

$2p(η) - ∑_t p(t)^2$

in the `Count` case (`p` the probablity mass function).

The predictions `ŷ` should be a vector of `UnivariateFinite` distributions from CategoricalDistritutions.jl, in the case of `Finite` target `y` (a `CategoricalVector`) and should otherwise be a supported `Distributions.UnivariateDistribution` such as `Normal` or `Poisson`.

See also [`BrierLoss`](@ref), which differs only in sign.

Any iterator with a `length` generating `Real` elements can be used for `weights`. The keys of `class_weights` should include all conceivable values for observations in `y`, and values should be `Real`. 

Measurements are aggregated. To obtain a separate measurement for each observation, use the syntax `measurements(BrierScore(), ŷ, y)`. Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Missing,T}` where `T` is `Continuous` or `Count` (for respectively continuous or discrete Distribution.jl objects in `ŷ`) or  `OrderedFactor` or `Multiclass` (for `UnivariateFinite` distributions in `ŷ`). 

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
human_name = brier score
```
