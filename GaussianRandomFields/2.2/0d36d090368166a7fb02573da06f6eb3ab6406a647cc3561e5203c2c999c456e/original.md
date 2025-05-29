```
plot_covariance_matrix(grf[, pts...])

Evaluate the covariance function of the Gaussian random field `grf` in the (optional) points `pts` and plot the result.
```

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=11)
0.0:0.1:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts, minpadding=7)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 11×11 structured grid, using a circulant embedding

julia> plot_covariance_matrix(grf);

julia> pts = range(0, stop=1, length=21)
0.0:0.05:1.0

julia> plot_covariance_matrix(grf, pts, pts);

```
