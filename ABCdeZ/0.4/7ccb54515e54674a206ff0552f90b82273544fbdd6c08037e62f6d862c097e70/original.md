```
Factored{N} <: Distribution{Multivariate, MixedSupport}
```

A `Distribution` type that can be used to combine multiple `UnivariateDistribution`'s (independently).

# Examples

```julia-repl
julia> prior = Factored(Normal(0, 1), Uniform(-1, 1))
Factored{2}(
p: (Normal{Float64}(μ=0.0, σ=1.0), Uniform{Float64}(a=-1.0, b=1.0))
)
```
