```
GaussianRandomField([mean,] cov, generator, pts...)
GaussianRandomField([mean,] cov, generator, nodes, elements)
```

Compute a Gaussian random field with mean `mean` and covariance structure `cov` defined in the points `pts`, and computed using the Gaussian random field generator `generator`.

# Examples

```jldoctest label2
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> mean = fill(π, (51, 51));

julia> grf = GaussianRandomField(mean, cov, Cholesky(), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a Cholesky decomposition

```

If no `mean` is specified, a zero-mean Gaussian random field is assumed.

```jldoctest label2
julia> grf = GaussianRandomField(cov, Cholesky(), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a Cholesky decomposition

```

The  Gaussian random field generator `generator` can be `Cholesky()`, `Spectral()`, `KarhunenLoeve(n)` (where `n` is the number of terms in the expansion), or `CirculantEmbedding()`. The points `pts` can be specified as arguments of type `AbstractVector`, in which case a tensor (Kronecker) product is assumed, or as a Finite Element mesh with node table `nodes` and element table `elements`.

```jldoctest label2
julia> grf = GaussianRandomField(cov, KarhunenLoeve(500), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 500 terms

julia> exponential_cov = CovarianceFunction(2, Exponential(.1))
2d exponential covariance function (λ=0.1, σ=1.0, p=2.0)

julia> grf = GaussianRandomField(exponential_cov, CirculantEmbedding(), pts, pts)
Gaussian random field with 2d exponential covariance function (λ=0.1, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

```

Separable Gaussian random fields can be defined using `SeparableCovarianceFunction`.

```jldoctest label2
julia> separable_cov = SeparableCovarianceFunction(Exponential(.1), Exponential(.1))
2d separable covariance function [ exponential (λ=0.1, σ=1.0, p=2.0), exponential (λ=0.1, σ=1.0, p=2.0) ]

julia> grf = GaussianRandomField(separable_cov, KarhunenLoeve(500), pts, pts)
Gaussian random field with 2d separable covariance function [ exponential (λ=0.1, σ=1.0, p=2.0), exponential (λ=0.1, σ=1.0, p=2.0) ] on a 51×51 structured grid, using a KL expansion with 500 terms

julia> plot_eigenfunction(grf, 3);

```

We also offer support for anisotropic random fields.

```jldoctest label2
julia> anisotropic_cov = CovarianceFunction(2, AnisotropicExponential([500 400; 400 500]))
2d anisotropic exponential covariance function (A=[500 400; 400 500], σ=1.0)

julia> grf = GaussianRandomField(anisotropic_cov, CirculantEmbedding() , pts, pts)
Gaussian random field with 2d anisotropic exponential covariance function (A=[500 400; 400 500], σ=1.0) on a 51×51 structured grid, using a circulant embedding

julia> heatmap(grf);

```

For irregular domains, specify the points as matrices containing the `nodes` and `elements` of a finite element mesh. To compute the value of the random field at the element centers, use the optional keyword `mode="center"`.

```jldoctest label2
julia> nodes, elements = Lshape();

julia> grf = GaussianRandomField(cov, Spectral(), nodes, elements)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a mesh with 998 points and 1861 elements, using a spectral decomposition

```

Alternativly, simply pass a `Matrix{T}` of size `N` by `d` to compute the random field at un unstructured grid defined by the given set of points.

Samples from the random field can be computed using the `sample` function.

```jldoctest label2
julia> sample(grf);

```

See also: [`Cholesky`](@ref), [`Spectral`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref), [`sample`](@ref)
