```
ICA
```

A model type for constructing a independent component analysis model, based on [MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
ICA = @load ICA pkg=MultivariateStats
```

Do `model = ICA()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `ICA(outdim=...)`.

Independent component analysis is a computational technique for separating a multivariate signal into additive subcomponents, with the assumption that the subcomponents are non-Gaussian and independent from each other.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Continuous`; check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `outdim::Int=0`: The number of independent components to recover, set automatically if `0`.
  * `alg::Symbol=:fastica`: The algorithm to use (only `:fastica` is supported at the moment).
  * `fun::Symbol=:tanh`: The approximate neg-entropy function, one of `:tanh`, `:gaus`.
  * `do_whiten::Bool=true`: Whether or not to perform pre-whitening.
  * `maxiter::Int=100`: The maximum number of iterations.
  * `tol::Real=1e-6`: The convergence tolerance for change in the unmixing matrix W.
  * `mean::Union{Nothing, Real, Vector{Float64}}=nothing`: mean to use, if nothing (default) centering is computed and applied, if zero, no centering; otherwise a vector of means can be passed.
  * `winit::Union{Nothing,Matrix{<:Real}}=nothing`: Initial guess for the unmixing matrix `W`: either an empty matrix (for random initialization of `W`), a matrix of size `m × k` (if `do_whiten` is true), or a matrix of size `m × k`. Here `m` is the number of components (columns) of the input.

# Operations

  * `transform(mach, Xnew)`: Return the component-separated version of input `Xnew`, which should have the same scitype as `X` above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `projection`: The estimated component matrix.
  * `mean`: The estimated mean vector.

# Report

The fields of `report(mach)` are:

  * `indim`: Dimension (number of columns) of the training data and new data to be transformed.
  * `outdim`: Dimension of transformed data.
  * `mean`: The mean of the untransformed training data, of length `indim`.

# Examples

```
using MLJ

ICA = @load ICA pkg=MultivariateStats

times = range(0, 8, length=2000)

sine_wave = sin.(2*times)
square_wave = sign.(sin.(3*times))
sawtooth_wave = map(t -> mod(2t, 2) - 1, times)
signals = hcat(sine_wave, square_wave, sawtooth_wave)
noisy_signals = signals + 0.2*randn(size(signals))

mixing_matrix = [ 1 1 1; 0.5 2 1; 1.5 1 2]
X = MLJ.table(noisy_signals*mixing_matrix)

model = ICA(outdim = 3, tol=0.1)
mach = machine(model, X) |> fit!

X_unmixed = transform(mach, X)

using Plots

plot(X.x2)
plot(X.x2)
plot(X.x3)

plot(X_unmixed.x1)
plot(X_unmixed.x2)
plot(X_unmixed.x3)

```

See also [`PCA`](@ref), [`KernelPCA`](@ref), [`FactorAnalysis`](@ref), [`PPCA`](@ref)
