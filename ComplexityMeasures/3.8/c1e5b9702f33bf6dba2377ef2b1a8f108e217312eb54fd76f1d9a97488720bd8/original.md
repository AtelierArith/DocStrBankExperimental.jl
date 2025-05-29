```
DiscreteInfoEstimator
```

The supertype of all discrete information measure estimators, which are used in combination with a [`ProbabilitiesEstimator`](@ref) as input to  [`information`](@ref) or related functions.

The first argument to a discrete estimator is always an [`InformationMeasure`](@ref) (defaults to [`Shannon`](@ref)).

## Description

A discrete [`InformationMeasure`](@ref) is a functional of a probability mass function. To estimate such a measure from data, we must first estimate a probability mass function using a [`ProbabilitiesEstimator`](@ref) from the (encoded/discretized) input data, and then apply the estimator to the estimated probabilities. For example, the [`Shannon`](@ref) entropy is typically computed using the [`RelativeAmount`](@ref) estimator to compute probabilities, which are then given to the [`PlugIn`](@ref) estimator. Many other estimators exist, not only for [`Shannon`](@ref) entropy, but other information measures as well.

We provide a library of both generic estimators such as [`PlugIn`](@ref) or [`Jackknife`](@ref) (which can be applied to any measure), as well as dedicated estimators such as [`MillerMadow`](@ref), which computes [`Shannon`](@ref) entropy using the Miller-Madow bias correction. The list below gives a complete overview.

## Implementations

The following estimators are generic and can compute any [`InformationMeasure`](@ref).

  * [`PlugIn`](@ref). The default, generic plug-in estimator of any information measure.   It computes the measure exactly as stated in the definition, using the computed   probability mass function.
  * [`Jackknife`](@ref). Uses the a combination of the plug-in estimator and the jackknife   principle to estimate the information measure.

### [`Shannon`](@ref) entropy estimators

The following estimators are dedicated [`Shannon`](@ref) entropy estimators, which provide improvements over the naive [`PlugIn`](@ref) estimator.

  * [`MillerMadow`](@ref).
  * [`HorvitzThompson`](@ref).
  * [`Schuermann`](@ref).
  * [`GeneralizedSchuermann`](@ref).
  * [`ChaoShen`](@ref).

!!! info
    Any of the implemented [`DiscreteInfoEstimator`](@ref)s can be used in combination with *any* [`ProbabilitiesEstimator`](@ref) as input to [`information`](@ref). What this means is that every estimator actually comes in many different variants - one for each [`ProbabilitiesEstimator`](@ref). For example, the [`MillerMadow`](@ref) estimator of [`Shannon`](@ref) entropy is typically calculated with [`RelativeAmount`](@ref) probabilities. But here, you can use for example the [`BayesianRegularization`](@ref) or the [`Shrinkage`](@ref) probabilities estimators instead, i.e. `information(MillerMadow(), RelativeAmount(outcome_space), x)` and `information(MillerMadow(), BayesianRegularization(outcomes_space), x)` are distinct estimators. This holds for all [`DiscreteInfoEstimator`](@ref)s. Many of these estimators haven't been explored in the literature before, so feel free to explore, and please cite this software if you use it to explore some new estimator combination!

