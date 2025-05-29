```
Spectral()
```

Returns a [`GaussianRandomFieldGenerator`](@ref) based on a spectral (eigenvalue) decomposition of the covariance matrix.

# Optional Arguments for `GaussianRandomField`

  * `n::Integer`: the number of eigenvalues to compute. By default, we compute all eigenvalues.
  * `eigensolver::EigenSolver`: which method to use for the eigenvalue decomposition (see [`AbstractEigenSolver`](@ref)). The default is `EigenSolver()`.

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, Spectral(), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a spectral decomposition

julia> heatmap(grf);

```

!!! tip
    Try using the Karhunen-Loève expansion if evaluating the covariance matrix is too expensive.


This is also useful when computing Gaussian random fields on a Finite Element mesh using a truncated KL expansion. Here's an example that computes the first 10 eigenfunctions on an L-shaped domain.

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> p, t = Lshape();

julia> grf = GaussianRandomField(cov, Spectral(), p, t, n=10)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a mesh with 998 points and 1861 elements, using a spectral decomposition

```

See also: [`Cholesky`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref)
