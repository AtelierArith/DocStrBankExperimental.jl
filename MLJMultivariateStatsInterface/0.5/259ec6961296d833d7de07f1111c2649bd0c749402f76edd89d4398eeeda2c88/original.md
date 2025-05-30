```
PCA
```

A model type for constructing a pca, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
PCA = @load PCA pkg=MultivariateStats
```

Do `model = PCA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `PCA(maxoutdim=...)`.

Principal component analysis learns a linear projection onto a lower dimensional space while preserving most of the initial variance seen in the training data.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Continuous`; check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `maxoutdim=0`: Together with `variance_ratio`, controls the output dimension `outdim` chosen by the model. Specifically, suppose that `k` is the smallest integer such that retaining the `k` most significant principal components accounts for `variance_ratio` of the total variance in the training data. Then `outdim = min(outdim, maxoutdim)`. If `maxoutdim=0` (default) then the effective `maxoutdim` is `min(n, indim - 1)` where `n` is the number of observations and `indim` the number of features in the training data.
  * `variance_ratio::Float64=0.99`: The ratio of variance preserved after the transformation
  * `method=:auto`: The method to use to solve the problem. Choices are

      * `:svd`: Support Vector Decomposition of the matrix.
      * `:cov`: Covariance matrix decomposition.
      * `:auto`: Use `:cov` if the matrices first dimension is smaller than its second dimension and otherwise use `:svd`
  * `mean=nothing`: if `nothing`, centering will be computed and applied, if set to `0` no centering (data is assumed pre-centered); if a vector is passed, the centering is done with that vector.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which should have the same scitype as `X` above.
  * `inverse_transform(mach, Xsmall)`: For a dimension-reduced table `Xsmall`, such as returned by `transform`, reconstruct a table, having same the number of columns as the original training data `X`, that transforms to `Xsmall`. Mathematically, `inverse_transform` is a right-inverse for the PCA projection map, whose image is orthogonal to the kernel of that map. In particular, if `Xsmall = transform(mach, Xnew)`, then `inverse_transform(Xsmall)` is only an approximation to `Xnew`.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `projection`: Returns the projection matrix, which has size `(indim, outdim)`, where `indim` and `outdim` are the number of features of the input and output respectively.

# Report

The fields of `report(mach)` are:

  * `indim`: Dimension (number of columns) of the training data and new data to be transformed.
  * `outdim = min(n, indim, maxoutdim)` is the output dimension; here `n` is the number of observations.
  * `tprincipalvar`: Total variance of the principal components.
  * `tresidualvar`: Total residual variance.
  * `tvar`: Total observation variance (principal + residual variance).
  * `mean`: The mean of the untransformed training data, of length `indim`.
  * `principalvars`: The variance of the principal components. An AbstractVector of length `outdim`
  * `loadings`: The models loadings, weights for each variable used when calculating principal components. A matrix of size (`indim`, `outdim`) where `indim` and `outdim` are as defined above.

# Examples

```
using MLJ

PCA = @load PCA pkg=MultivariateStats

X, y = @load_iris # a table and a vector

model = PCA(maxoutdim=2)
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

See also [`KernelPCA`](@ref), [`ICA`](@ref), [`FactorAnalysis`](@ref), [`PPCA`](@ref)
