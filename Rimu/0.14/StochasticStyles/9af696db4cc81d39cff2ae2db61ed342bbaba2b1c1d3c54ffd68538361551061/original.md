```
IsStochasticWithThreshold{T=Float64}(threshold=1.0) <: StochasticStyle{T}
```

Stochastic propagation with floating point walker numbers. During the vector matrix product each individual diagonal and spawning result is rounded stochastically if smaller than `threshold` (before annihilations). For a more customizable stochastic style, see [`IsDynamicSemistochastic`](@ref).

See also [`StochasticStyle`](@ref).
