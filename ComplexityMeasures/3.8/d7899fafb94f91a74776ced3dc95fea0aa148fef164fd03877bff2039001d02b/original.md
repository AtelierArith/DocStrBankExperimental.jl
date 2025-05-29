```
AddConstant <: ProbabilitiesEstimator
AddConstant(; c = 1.0)
```

A generic add-constant probabilities estimator for counting-based [`OutcomeSpace`](@ref)s, where several literature estimators can be obtained tuning `c`. Currently $c$ can only be a scalar.

  * `c = 1.0` is the Laplace estimator, or the "add-one" estimator.

## Description

Probabilities for the $k$-th outcome $\omega_{k}$ are estimated as

$$
p(\omega_k) = \dfrac{(n_k + c)}{n + mc},
$$

where $m$ is the cardinality of the outcome space, and $n$ is the number of (encoded) input data points, and $n_k$ is the number of times the outcome $\omega_{k}$ is observed in the (encoded) input data points.

If the `AddConstant` estimator used with [`probabilities_and_outcomes`](@ref), then $m$ is set to the number of *observed* outcomes. If used with [`allprobabilities_and_outcomes`](@ref), then $m$ is set to the number of *possible* outcomes.

!!! note "Unobserved outcomes are assigned nonzero probability!"
    Looking at the formula above, if $n_k = 0$, then unobserved outcomes are assigned a non-zero probability of $\dfrac{c}{n + mc}$. This means that if the estimator is used with [`allprobabilities_and_outcomes`](@ref), then all outcomes, even those that are not observed, are assigned non-zero probabilities. This might affect your results if using e.g. [`missing_outcomes`](@ref).

