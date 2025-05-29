```
CirculantEmbedding()
```

Returns a [`GaussianRandomFieldGenerator`](@ref) that uses FFTs to compute samples of the Gaussian random field.

!!! warning
    Circulant embedding can only be applied if the points are specified on a structured grid.


# Optional Arguments for `GaussianRandomField`

  * `minnpadding::Integer`: minimum amount of padding.
  * `measure::Bool`: optimize the FFT to increase the efficiency of the [`sample`](@ref) method. Default is `true`.
  * `primes::Bool`: the size of the minimum circulant embedding of the covariance matrix can be written as a product of small primes (2, 3, 5 and 7). Default is `false`.

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.1, 1))
2d Matérn covariance function (λ=0.1, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.1, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

julia> contourf(grf);

julia> plot_eigenvalues(grf);

```

!!! note
    With appropriate ordering, the covariance matrix of a Gaussian random field is a (nested block) Toeplitz matrix. This matrix can be embedded into a larger (nested block) circulant matrix, whose eigenvalues can be rapidly computed using FFT. A difficulty here is that although the covariance matrix is positive semi-definite, its circulant extension in general is not. As a remedy, one can add so-called *ghost points* outside the domain of interest using the optional flag `minpadding`.


```jldoctest; filter=r"^[┌│└].*$"s
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts);
┌ Warning: 318 negative eigenvalues ≥ -0.5828339433508111 detected, Gaussian random field will be 
│         approximated (ignoring all negative eigenvalues); increase padding if possible
└ @ GaussianRandomFields ~/.julia/dev/GaussianRandomFields/src/generators/circulant_embedding.jl:94
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts, minpadding=79)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

```

See also: [`Cholesky`](@ref), [`Spectral`](@ref), [`KarhunenLoeve`](@ref)
