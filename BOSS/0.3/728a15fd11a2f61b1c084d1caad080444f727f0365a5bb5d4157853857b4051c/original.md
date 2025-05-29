```
LinModel(; kwargs...)
```

A parametric surrogate model linear in its parameters.

This model definition will provide better performance than the more general 'NonlinModel' in the future. This feature is not implemented yet so it is equivalent to using `NonlinModel` for now.

The linear model is defined as

```
    ϕs = lift(x)
    y = [θs[i]' * ϕs[i] for i in 1:m]
```

where

```
    x = [x₁, ..., xₙ]
    y = [y₁, ..., yₘ]
    θs = [θ₁, ..., θₘ], θᵢ = [θᵢ₁, ..., θᵢₚ]
    ϕs = [ϕ₁, ..., ϕₘ], ϕᵢ = [ϕᵢ₁, ..., ϕᵢₚ]
```

and $n, m, p ∈ R$.

# Keywords

  * `lift::Function`: Defines the `lift` function `(::Vector{<:Real}) -> (::Vector{Vector{<:Real}})`       according to the definition above.
  * `theta_priors::AbstractVector{<:UnivariateDistribution}`: The prior distributions for       the parameters `[θ₁₁, ..., θ₁ₚ, ..., θₘ₁, ..., θₘₚ]` according to the definition above.
  * `noise_std_priors::NoiseStdPriors`: The prior distributions       of the noise standard deviations of each `y` dimension.
