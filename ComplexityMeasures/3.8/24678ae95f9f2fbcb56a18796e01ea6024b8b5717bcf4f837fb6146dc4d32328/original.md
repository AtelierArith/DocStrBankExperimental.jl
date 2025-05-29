```
RelativeAmount <: ProbabilitiesEstimator
RelativeAmount()
```

The `RelativeAmount` estimator is used with [`probabilities`](@ref) and related functions to estimate probabilities over the given [`OutcomeSpace`](@ref) using maximum likelihood estimation (MLE), also called plug-in estimation. See [`ProbabilitiesEstimator`](@ref) for usage.

## Description

Consider a length-`m` outcome space $\Omega$ and random sample of length `N`. The maximum likelihood estimate of the probability of the `k`-th outcome $\omega_k$ is

$$
p(\omega_k) = \dfrac{n_k}{N},
$$

where $n_k$ is the number of times the `k`-th outcome was observed in the (encoded) sample.

This estimation is known as *maximum likelihood estimation*. However, `RelativeAmount` also serves as the fall-back probabilities estimator for [`OutcomeSpace`](@ref)s that are not count-based and only yield "pseudo-counts", for example [`WaveletOverlap`](@ref) or [`PowerSpectrum`](@ref). These outcome spaces do not yield counts, but pre-normalized numbers that can be treated as "relative frequencies" or "relative power". Hence, this estimator is called `RelativeAmount`.

## Examples

```julia
using ComplexityMeasures
x = cumsum(randn(100))
ps = probabilities(OrdinalPatterns{3}(), x) # `RelativeAmount` is the default estimator
ps_mle = probabilities(RelativeAmount(), OrdinalPatterns{3}(), x) # equivalent
ps == ps_mle # true
```

See also: [`BayesianRegularization`](@ref), [`Shrinkage`](@ref).
