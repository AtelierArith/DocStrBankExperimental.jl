```
probabilities_and_outcomes(
    [est::ProbabilitiesEstimator], o::OutcomeSpace, x::Array_or_SSSet
) → (p::Probabilities, Ω)
```

Estimate a probability distribution over the set of possible outcomes `Ω` defined by the [`OutcomeSpace`](@ref) `o`, given input data `x`. Probabilities are estimated according to the given probabilities estimator `est`, which defaults to [`RelativeAmount`](@ref).

The input data is typically an `Array` or a `StateSpaceSet` (or `SSSet` for short); see [Input data for ComplexityMeasures.jl](@ref input_data). Configuration options are always given as arguments to the chosen outcome space and probabilities estimator.

Return a tuple where the first element is a [`Probabilities`](@ref) instance, which is vector-like and contains the probabilities, and where the second element `Ω` are the outcomes corresponding to the probabilities, such that `p[i]` is the probability for the outcome `Ω[i]`.

The outcomes are actually included in `p`, and you can use the [`outcomes`](@ref) function on the `p` to get them. `probabilities_and_outcomes` returns both for backwards compatibility.

```
probabilities_and_outcomes(
    [est::ProbabilitiesEstimator], counts::Counts
) → (p::Probabilities, Ω)
```

Estimate probabilities from the pre-computed `counts` using the given [`ProbabilitiesEstimator`](@ref) `est`.

## Description

Probabilities are computed by:

1. Discretizing/encoding `x` into a finite set of outcomes `Ω` specified by the provided  [`OutcomeSpace`](@ref) `o`.
2. Assigning to each outcome `Ωᵢ ∈ Ω` either a count (how often it appears among the  discretized data points), or a pseudo-count (some pre-normalized probability such  that `sum(Ωᵢ for Ωᵢ in Ω) == 1`).

For outcome spaces that result in pseudo counts, such as [`PowerSpectrum`](@ref), these pseudo counts are simply treated as probabilities and returned directly (that is, `est` is ignored). For counting-based outcome spaces (see [`OutcomeSpace`](@ref) docstring), probabilities are estimated from the counts using some [`ProbabilitiesEstimator`](@ref) (first signature).

## Observed vs all probabilities

Due to performance optimizations, whether the returned probabilities contain `0`s as entries or not depends on the outcome space. E.g., in [`ValueBinning`](@ref) `0`s are skipped, while in [`PowerSpectrum`](@ref) `0` are not skipped, because we get them for free.

Use [`allprobabilities_and_outcomes`](@ref) to guarantee that zero probabilities are also returned (may be slower).
