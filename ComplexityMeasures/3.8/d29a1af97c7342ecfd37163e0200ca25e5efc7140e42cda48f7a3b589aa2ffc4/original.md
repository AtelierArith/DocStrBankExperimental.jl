```
ProbabilitiesEstimator
```

The supertype for all probabilities estimators.

The role of the probabilities estimator is to convert (pseudo-)counts to probabilities. Currently, the implementation of all probabilities estimators assume *finite* outcome space with known cardinality. Therefore, `ProbabilitiesEstimator` accept an [`OutcomeSpace`](@ref) as the first argument, which specifies the set of possible outcomes.

Probabilities estimators are used with [`probabilities`](@ref) and [`allprobabilities_and_outcomes`](@ref).

## Implementations

The default probabilities estimator is [`RelativeAmount`](@ref), which is compatible with any [`OutcomeSpace`](@ref). The following estimators only support counting-based outcomes.

  * [`Shrinkage`](@ref).
  * [`BayesianRegularization`](@ref).
  * [`AddConstant`](@ref).

## Description

In ComplexityMeasures.jl, probability mass functions are estimated from data by defining a set of possible outcomes $\Omega = \{\omega_1, \omega_2, \ldots, \omega_L \}$ (by specifying an [`OutcomeSpace`](@ref)), and assigning to each outcome $\omega_i$ a probability $p(\omega_i)$, such that $\sum_{i=1}^N p(\omega_i) = 1$ (by specifying a `ProbabilitiesEstimator`).
