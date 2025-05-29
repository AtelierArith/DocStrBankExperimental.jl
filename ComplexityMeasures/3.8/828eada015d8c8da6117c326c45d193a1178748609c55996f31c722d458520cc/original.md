```
entropy_approx(x; m = 2, τ = 1, r = 0.2 * Statistics.std(x), base = MathConstants.e)
```

Convenience syntax for computing the approximate entropy (Pincus, 1991) for timeseries `x`.

This is just a wrapper for `complexity(ApproximateEntropy(; m, τ, r, base), x)` (see also [`ApproximateEntropy`](@ref)).
