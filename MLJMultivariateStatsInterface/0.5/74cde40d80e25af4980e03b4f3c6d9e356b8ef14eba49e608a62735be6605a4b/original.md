```
FactorAnalysis
```

A model type for constructing a factor analysis model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
FactorAnalysis = @load FactorAnalysis pkg=MultivariateStats
```

Do `model = FactorAnalysis()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `FactorAnalysis(method=...)`.

Factor analysis is a linear-Gaussian latent variable model that is closely related to probabilistic PCA. In contrast to the probabilistic PCA model, the covariance of conditional distribution of the observed variable given the latent variable is diagonal rather than isotropic.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns   are of scitype `Continuous`; check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `method::Symbol=:cm`: Method to use to solve the problem, one of `:ml`, `:em`, `:bayes`.
  * `maxoutdim=0`: Controls the the dimension (number of columns) of the output,   `outdim`. Specifically, `outdim = min(n, indim, maxoutdim)`, where `n` is the number of   observations and `indim` the input dimension.
  * `maxiter::Int=1000`: Maximum number of iterations.
  * `tol::Real=1e-6`: Convergence tolerance.
  * `eta::Real=tol`: Variance lower bound.
  * `mean::Union{Nothing, Real, Vector{Float64}}=nothing`: If `nothing`, centering will be   computed and applied; if set to `0` no centering is applied (data is assumed   pre-centered); if a vector, the centering is done with that vector.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which should have the same scitype as `X` above.
  * `inverse_transform(mach, Xsmall)`: For a dimension-reduced table `Xsmall`, such as returned by `transform`, reconstruct a table, having same the number of columns as the original training data `X`, that transforms to `Xsmall`. Mathematically, `inverse_transform` is a right-inverse for the PCA projection map, whose image is orthogonal to the kernel of that map. In particular, if `Xsmall = transform(mach, Xnew)`, then `inverse_transform(Xsmall)` is only an approximation to `Xnew`.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `projection`: Returns the projection matrix, which has size `(indim, outdim)`, where `indim` and `outdim` are the number of features of the input and ouput respectively. Each column of the projection matrix corresponds to a factor.

# Report

The fields of `report(mach)` are:

  * `indim`: Dimension (number of columns) of the training data and new data to be transformed.
  * `outdim`: Dimension of transformed data (number of factors).
  * `variance`: The variance of the factors.
  * `covariance_matrix`: The estimated covariance matrix.
  * `mean`: The mean of the untransformed training data, of length `indim`.
  * `loadings`: The factor loadings. A matrix of size (`indim`, `outdim`) where `indim` and `outdim` are as defined above.

# Examples

```
using MLJ

FactorAnalysis = @load FactorAnalysis pkg=MultivariateStats

X, y = @load_iris # a table and a vector

model = FactorAnalysis(maxoutdim=2)
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

See also [`KernelPCA`](@ref), [`ICA`](@ref), [`PPCA`](@ref), [`PCA`](@ref)
