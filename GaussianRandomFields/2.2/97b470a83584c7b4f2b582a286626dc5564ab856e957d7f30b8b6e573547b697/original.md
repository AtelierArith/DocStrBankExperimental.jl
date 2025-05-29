```
Cholesky()
```

Retuns a [`GaussianRandomFieldGenerator`](@ref) based on a Cholesky factorization of the covariance matrix.

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51) 
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, Cholesky(), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a Cholesky decomposition

julia> heatmap(grf);

```

!!! warning
    The Cholesky factorization requires the covariance matrix to be symmetric and positive definite. If the covariance matrix is not positive definite, an error will be thrown. Try using the `Spectral` method in that case.


See also: [`Spectral`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref)
