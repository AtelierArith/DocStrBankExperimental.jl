```
empirical_distribution(E::DifferentiableExpectation, θ...; kwargs...)
```

Return a uniform [`FixedAtomsProbabilityDistribution`](@ref) over `{f(x₁), ..., f(xₛ)}`, where the `xᵢ ∼ p(θ)` are iid samples.
