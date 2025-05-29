```
sample(grf)
    sample(grf[, xi])
```

Take a sample from the Gaussian random field `grf` using the (optional) normally distributed random numbers `xi`. The vector`xi` must have appropriate length.

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Whittle(.1))
2d Whittle covariance function (λ=0.1, σ=1.0, p=2.0)

julia> pts = pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts)
Gaussian random field with 2d Whittle covariance function (λ=0.1, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

julia> sample(grf);

julia> sample(grf, xi=randn(randdim(grf)));
```

See also: [`GaussianRandomField`](@ref), [`Matern`](@ref), [`CovarianceFunction`](@ref), [`CirculantEmbedding`]
