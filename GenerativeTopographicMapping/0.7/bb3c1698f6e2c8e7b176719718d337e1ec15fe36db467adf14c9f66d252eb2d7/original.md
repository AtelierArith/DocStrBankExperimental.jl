```
GTM
```

A model type for constructing a gtm, based on [GenerativeTopographicMapping.jl](https://github.com/john-waczak/GenerativeTopographicMapping.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
GTM = @load GTM pkg=GenerativeTopographicMapping
```

Do `model = GTM()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `GTM(k=...)`.

GenerativeTopographicMapping implements [Generative Topographic Mapping](https://direct.mit.edu/neco/article/10/1/215-234/6127),   Neural Computation; Bishop, C.; (1998):   "GTM: The Generative Topographic Mapping"

# Training data

In MLJ or MLJBase, bind an instance `model` to data with     mach = machine(model, X) where

  * `X`: `Table` of input features whose columns are of scitype `Continuous.`

Train the machine with `fit!(mach, rows=...)`.

# Hyper-parameters

  * `k=16`: Number of nodes along once side of GTM latent grid. There are `k²` total nodes.
  * `m=4`:  There are `m²` total RBFs.
  * `s=2.0`: Scale factor for RBF variance.
  * `α=0.1`:  Model weight regularization parameter (0.0 for no regularization)
  * `topology=:square`: Topology of latent space. One of `:square`, `:cylinder`, or `:torus`
  * `tol=0.1`: Tolerance used for determining convergence during expectation-maximization fitting.
  * `nepochs=100`: Maximum number of training epochs.
  * `nrepeats=4`: Number of steps to repeat at/below `tol` before GTM is considered converged.
  * `rand_init=false`: Whether or not to randomly initialize weight matrix `W`. If false, `W` is initialized using first two principal components of the dataset.

# Operations

  * `transform(mach, X)`: returns the coordinates `ξ₁` and `ξ₂` cooresponding to the mean of the latent node responsibility distribution.
  * `predict(mach, X)`: returns the index of the node corresponding to the mode of the latent node responsibility distribution.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `gtm`: The `GenerativeTopographicMap` object fit by the `GTM` model. Contains node coordinates, RBF means, RBF variance, weights, etc.

# Report

The fields of `report(mach)` are:

  * `W`: the fitted GTM weight matrix
  * `β⁻¹`: the fitted GTM variance
  * `Φ`: the node RBF activation matrix
  * `Ξ`: the node coordinates in the latent space
  * `Ψ`: the projected node means in the data space
  * `llhs`: the log-likelihood values from each iteration of the training loop
  * `converged`: is `true` if the convergence critera were met before reaching `niter`
  * `AIC`: the Aikike Information Criterion
  * `BIC`: the Bayesian Information Criterion

# Examples

```
using MLJ
gtm = @load GTM pkg=GenerativeTopographicMapping
model = gtm()
X, y = make_blob(100, 10; centers=5) # synthetic data
mach = machine(model, X) |> fit!
X̃ = transform(mach, X)

rpt = report(mach)
classes = rpt.classes
```
