```
GSMLinear
```

A model type for constructing a gsm linear, based on [GenerativeTopographicMapping.jl](https://github.com/john-waczak/GenerativeTopographicMapping.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
GSMLinear = @load GSMLinear pkg=GenerativeTopographicMapping
```

Do `model = GSMLinear()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `GSMLinear(k=...)`.

Generative Simplex Mapping based based on [Generative Topographic Mapping](https://direct.mit.edu/neco/article/10/1/215-234/6127),   Neural Computation; Bishop, C.; (1998):   "GTM: The Generative Topographic Mapping" where the latent points are configured as a gridded n-simplex.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with     mach = machine(model, X) where

  * `X`: `Table` of input features whose columns are of scitype `Continuous.`

Train the machine with `fit!(mach, rows=...)`.

# Hyper-parameters

  * `k=10`: Number of latent nodes per edge in the latent space simplex grid.
  * `Nv=3`: Number of vertices for the simplex i.e. the number of endmembers.
  * `λ=0.1`:  Model weight regularization parameter.
  * `make_positive=false`:
  * `nepochs=100`: Maximum number of training epochs.
  * `tol=0.1`: Tolerance used for determining convergence during expectation-maximization fitting.
  * `nconverged=4`: Number of steps to repeat at/below `tol` before GSMLinear is considered converged.
  * `rng=123`: random seed or random number generator used for model weight initialization.

# Operations

  * `transform(mach, X)`: returns the coordinates `ξᵢ` cooresponding to the mean of the latent node responsibility distribution.
  * `predict(mach, X)`: returns the index of the node corresponding to the mode of the latent node responsibility distribution.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `gsm`: The `GenerativeSimplexMap` object fit by the `GSMLinear` model. Contains node coordinates, RBF means, RBF variance, weights, etc.

# Report

The fields of `report(mach)` are:

  * `W`: the fitted GTM weight matrix
  * `β⁻¹`: the fitted GTM variance
  * `Φ`: the node RBF activation matrix
  * `node_data_means`: the projected node means in the data space
  * `Z`: the node coordinates in the latent space
  * `Q`: Objective function maximized during EM routine
  * `llhs`: the log-likelihood values from each iteration of the training loop
  * `converged`: is `true` if the convergence critera were met before reaching `niter`
  * `AIC`: the Aikike Information Criterion
  * `BIC`: the Bayesian Information Criterion

# Examples

```
using MLJ
gsm = @load GSMLinear pkg=GenerativeTopographicMapping
model = gsm()
X, y = make_blob(100, 10; centers=5) # synthetic data
mach = machine(model, X) |> fit!
X̃ = transform(mach, X)

rpt = report(mach)
classes = rpt.classes
```
