```
entropy_sample(x; r = 0.2std(x), m = 2, τ = 1, normalize = true)
```

Convenience syntax for estimating the (normalized) sample entropy (Richman & Moorman, 2000) of timeseries `x`.

This is just a wrapper for `complexity(SampleEntropy(; r, m, τ, base), x)`.

See also: [`SampleEntropy`](@ref), [`complexity`](@ref), [`complexity_normalized`](@ref)).
