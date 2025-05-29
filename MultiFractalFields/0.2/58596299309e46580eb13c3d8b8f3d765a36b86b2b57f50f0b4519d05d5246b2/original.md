```
GaussianField(cov, torus)
```

Gaussian random field with covariance `cov` on the `torus`.

# Examples

```jldoctest
julia> torus = Torus(100, 0.1)
Torus{Float64, Float64}(n=100,η=0.1)

julia> lincov = Linear(0.5)
Linear{Float64}(ξ=0.5, λ=1.0, σ²=1.0)

julia> GaussianField(lincov ,torus)
GaussianField(cov=Linear{Float64}(ξ=0.5, λ=1.0, σ²=1.0),torus=Torus{Float64, Float64}(n=100,η=0.1))
```
