```
Exponential(ξ, [λ = 1], [σ² = 1])
```

Exponential covariance function with scaling exponent `ξ`, correlation length `λ` and variance `σ²`.

It is defined as $C(r)= \sigma^2  e^{-\left(\frac{r}{\lambda}\right)^{\xi}}$.

# Examples

```jldoctest
julia> expcov = Exponential(0.5, 1.5, 3)
Exponential{Float64}(ξ=0.5, λ=1.5, σ²=3.0)

julia> expcov(0)
3.0

julia> expcov(1.5) == 3/ℯ
true
```
