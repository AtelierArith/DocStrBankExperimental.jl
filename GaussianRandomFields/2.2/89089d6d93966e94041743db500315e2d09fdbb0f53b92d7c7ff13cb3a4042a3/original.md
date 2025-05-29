```
plot_eigenvalues(grf)
```

Log-log plot of the eigenvalues of the Gaussian random field. Only available for Gaussian random field generators of type `Spectral`, `KarhunenLoeve` and `CirculantEmbedding`.

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Gaussian(.1))
2d Gaussian covariance function (λ=0.1, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(100), pts, pts)
Gaussian random field with 2d Gaussian covariance function (λ=0.1, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 100 terms

julia> plot_eigenvalues(grf);

```

See also: [`plot_eigenfunction`](@ref)
