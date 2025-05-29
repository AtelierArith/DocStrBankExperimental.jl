```
BayesianRegularization <: ProbabilitiesEstimator
BayesianRegularization(; a = 1.0)
```

The `BayesianRegularization` estimator is used with [`probabilities`](@ref) and related functions to estimate probabilities an `m`-element counting-based [`OutcomeSpace`](@ref) using Bayesian regularization of cell counts [Hausser2009](@cite). See [`ProbabilitiesEstimator`](@ref) for usage.

## Outcome space requirements

This estimator only works with counting-compatible outcome spaces.

## Description

The `BayesianRegularization` estimator estimates the probability of the $k$-th outcome $\omega_{k}$ is

$$
\omega_{k}^{\text{BayesianRegularization}} = \dfrac{n_k + a_k}{n + A},
$$

where $n$ is the number of samples in the input data, $n_k$ is the observed counts for the outcome $\omega_{k}$, and $A = \sum_{i=1}^k a_k$.

## Picking `a`

There are many common choices of priors, some of which are listed in [Hausser2009](@citet). They include

  * `a == 0`, which is equivalent to the [`RelativeAmount`](@ref) estimator.
  * `a == 0.5` (Jeffrey's prior)
  * `a == 1` (Bayes-Laplace uniform prior)

`a` can also be chosen as a vector of real numbers. Then, if used with [`allprobabilities_and_outcomes`](@ref), it is required that  `length(a) == total_outcomes(o, x)`, where `x` is the input data and `o` is the [`OutcomeSpace`](@ref). If used with [`probabilities`](@ref), then `length(a)` must match the number of *observed* outcomes (you can check this using [`probabilities_and_outcomes`](@ref)). The choice of `a` can severely impact the estimation errors of the probabilities, and the errors depend both on the choice of `a` and on the sampling scenario [Hausser2009](@cite).

## Assumptions

The `BayesianRegularization` estimator assumes a fixed and known `m`. Thus, using it with [`probabilities_and_outcomes`](@ref) and [`allprobabilities_and_outcomes`](@ref) will  yield different results, depending on whether all outcomes are observed in the input data or not. For [`probabilities_and_outcomes`](@ref), `m` is the number of *observed* outcomes. For [`allprobabilities_and_outcomes`](@ref), `m = total_outcomes(o, x)`, where `o` is the [`OutcomeSpace`](@ref) and `x` is the input data.

!!! note
    If used with [`allprobabilities_and_outcomes`](@ref), then outcomes which have not been observed may be assigned non-zero probabilities. This might affect your results if using e.g. [`missing_outcomes`](@ref).


## Examples

```julia
using ComplexityMeasures
x = cumsum(randn(100))
ps_bayes = probabilities(BayesianRegularization(a = 0.5), OrdinalPatterns{3}(), x)
```

See also: [`RelativeAmount`](@ref), [`Shrinkage`](@ref).
