```
empirical_distribution(E::DifferentiableExpectation, θ...; kwargs...)
```

一様な [`FixedAtomsProbabilityDistribution`](@ref) を `{f(x₁), ..., f(xₛ)}` 上で返します。ここで、`xᵢ ∼ p(θ)` は独立同分布のサンプルです。
