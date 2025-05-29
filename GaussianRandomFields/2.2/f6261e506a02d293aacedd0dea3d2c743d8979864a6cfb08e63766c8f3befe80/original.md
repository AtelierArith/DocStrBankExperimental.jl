```
KarhunenLoeve(n)
```

Returns a [`GaussianRandomFieldGenerator`](@ref) using a Karhunen-Loève (KL) expansion with `n` terms. 

# Optional Arguments for `GaussianRandomField`

  * `quad::QuadratureRule`: quadrature rule used for the integral equation (see [`QuadratureRule`](@ref)), default is `EOLE()`.
  * `nq::Integer`: number of quadrature points in each dimension, where we require `nq^d > n`. Default is `nq = ceil(n^(1/d))`.
  * `eigensolver::EigenSolver`: which method to use for the eigenvalue decomposition (see [`AbstractEigenSolver`](@ref)). The default is `EigenSolver()`.

# Examples

```jldoctest label1
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 300 terms

julia> plot_eigenvalues(grf); # plot the eigenvalue decay

julia> plot_eigenfunction(grf, 4); # plots the fourth eigenfunction

```

If more terms `n` are used in the expansion, the approximation becomes better.

```jldoctest label1; setup=:(import Random; Random.seed!(12345))
julia> for n in [1, 2, 5, 10, 20, 50, 100, 200, 500, 1000]
           grf = GaussianRandomField(cov, KarhunenLoeve(n), pts, pts)
           @printf "%.8f\n" rel_error(grf)
       end
0.69838285
0.45494187
0.23231278
0.10079295
0.02647020
0.00978427
0.00356549
0.00107191
0.00019810
0.00004085

```

!!! note
    Techniqually, the KL expansion is computed using the Nystrom method. For nonstructured grids, we use a bounding box approach. Try using the `Spectral` method if this is not what you want.


!!! warning
    To avoid an *end effect* in the eigenvalue decay, choose `nq^d ≥ 5n`.


```jldoctest label1
julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts, quad=GaussLegendre())
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 300 terms

julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts, nq=40)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 300 terms

```

See also: [`Cholesky`](@ref), [`Spectral`](@ref), [`CirculantEmbedding`](@ref)
