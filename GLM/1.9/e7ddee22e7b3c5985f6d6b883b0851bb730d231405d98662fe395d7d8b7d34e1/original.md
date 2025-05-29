```
devresid(D, y, μ::Real)
```

Return the squared deviance residual of `μ` from `y` for distribution `D`

The deviance of a GLM can be evaluated as the sum of the squared deviance residuals.  This is the principal use for these values.  The actual deviance residual, say for plotting, is the signed square root of this value

```julia
sign(y - μ) * sqrt(devresid(D, y, μ))
```

# Examples

```jldoctest; setup = :(using GLM: Bernoulli, Normal, devresid)
julia> devresid(Normal(), 0, 0.25) ≈ abs2(0.25)
true

julia> devresid(Bernoulli(), 1, 0.75) ≈ -2*log(0.75)
true

julia> devresid(Bernoulli(), 0, 0.25) ≈ -2*log1p(-0.25)
true
```
