```
KernelPCA
```

A model type for constructing a kernel prinicipal component analysis model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
KernelPCA = @load KernelPCA pkg=MultivariateStats
```

Do `model = KernelPCA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `KernelPCA(maxoutdim=...)`.

In kernel PCA the linear operations of ordinary principal component analysis are performed in a [reproducing Hilbert space](https://en.wikipedia.org/wiki/Reproducing_kernel_Hilbert_space).

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Continuous`; check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `maxoutdim=0`: Controls the the dimension (number of columns) of the output, `outdim`. Specifically, `outdim = min(n, indim, maxoutdim)`, where `n` is the number of observations and `indim` the input dimension.
  * `kernel::Function=(x,y)->x'y`: The kernel function, takes in 2 vector arguments x and y, returns a scalar value. Defaults to the dot product of `x` and `y`.
  * `solver::Symbol=:eig`: solver to use for the eigenvalues, one of `:eig`(default, uses `LinearAlgebra.eigen`), `:eigs`(uses `Arpack.eigs`).
  * `inverse::Bool=true`: perform calculations needed for inverse transform
  * `beta::Real=1.0`: strength of the ridge regression that learns the inverse transform when inverse is true.
  * `tol::Real=0.0`: Convergence tolerance for eigenvalue solver.
  * `maxiter::Int=300`: maximum number of iterations for eigenvalue solver.

# Operations

  * `transform(mach, Xnew)`: Return a lower dimensional projection of the input `Xnew`, which   should have the same scitype as `X` above.
  * `inverse_transform(mach, Xsmall)`: For a dimension-reduced table `Xsmall`, such as returned by `transform`, reconstruct a table, having same the number of columns as the original training data `X`, that transforms to `Xsmall`.  Mathematically, `inverse_transform` is a right-inverse for the PCA projection map, whose image is orthogonal to the kernel of that map. In particular, if `Xsmall = transform(mach, Xnew)`, then `inverse_transform(Xsmall)` is only an approximation to `Xnew`.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `projection`: Returns the projection matrix, which has size `(indim, outdim)`, where `indim` and `outdim` are the number of features of the input and ouput respectively.

# Report

The fields of `report(mach)` are:

  * `indim`: Dimension (number of columns) of the training data and new data to be transformed.
  * `outdim`: Dimension of transformed data.
  * `principalvars`: The variance of the principal components.

# Examples

```
using MLJ
using LinearAlgebra

KernelPCA = @load KernelPCA pkg=MultivariateStats

X, y = @load_iris # a table and a vector

function rbf_kernel(length_scale)
    return (x,y) -> norm(x-y)^2 / ((2 * length_scale)^2)
end

model = KernelPCA(maxoutdim=2, kernel=rbf_kernel(1))
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

See also [`PCA`](@ref), [`ICA`](@ref), [`FactorAnalysis`](@ref), [`PPCA`](@ref)
