```
Random.rand(M::Circle{ℝ}; vector_at = nothing, σ::Real=1.0)
```

If `vector_at` is `nothing`, return a random point on the [`Circle`](@ref) $\mathbb S^1$ by picking a random element from $[-\pi,\pi)$ uniformly.

If `vector_at` is not `nothing`, return a random tangent vector from the tangent space of the point `vector_at` on the [`Circle`](@ref) by using a normal distribution with mean 0 and standard deviation `σ`.
