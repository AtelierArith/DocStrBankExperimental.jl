```
AmplitudeAwareOrdinalPatterns <: OutcomeSpace
AmplitudeAwareOrdinalPatterns{m}(τ = 1, A = 0.5, lt = ComplexityMeasures.isless_rand)
```

A variant of [`OrdinalPatterns`](@ref) that also incorporates amplitude information, based on the amplitude-aware permutation entropy [Azami2016](@cite). The outcome space and arguments are the same as in [`OrdinalPatterns`](@ref).

## Description

Similarly to [`WeightedOrdinalPatterns`](@ref), a weight $w_i$ is attached to each ordinal pattern extracted from each state (or delay) vector $\mathbf{x}_i = (x_1^i, x_2^i, \ldots, x_m^i)$ as

$$
w_i = \dfrac{A}{m} \sum_{k=1}^m |x_k^i | + \dfrac{1-A}{d-1}
\sum_{k=2}^d |x_{k}^i - x_{k-1}^i|,
$$

with $0 \leq A \leq 1$. When $A=0$ , only internal differences between the elements of $\mathbf{x}_i$ are weighted. Only mean amplitude of the state vector elements are weighted when $A=1$. With, $0<A<1$, a combined weighting is used.
