```
noiseradius(x::AbstractVector, d::Int, τ, ρs, n = 1) → ρ
```

Use the proposed* algorithm of[^Small2001] to estimate optimal `ρ` value for [`PseudoPeriodic`](@ref) surrogates, where `ρs` is a vector of possible `ρ` values. *The paper is ambiguous about exactly what to calculate. Here we count how many times we have pairs of length-2 that are identical in `x` and its surrogate, but **are not** also part of pairs of length-3.

This function directly returns the arg-maximum of the evaluated distribution of these counts versus `ρ`, use `TimeseriesSurrogates._noiseradius` with same arguments to get the actual distribution. `n` means to repeat τhe evaluation `n` times, which increases accuracy.

[^Small2001]: Small et al., Surrogate test for pseudoperiodic time series data, [Physical Review Letters, 87(18)](https://doi.org/10.1103/PhysRevLett.87.188101)
