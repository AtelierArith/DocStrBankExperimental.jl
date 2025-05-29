EvoTreeCount(;kwargs...)

A model type for constructing a EvoTreeCount, based on [EvoTrees.jl](https://github.com/Evovest/EvoTrees.jl), and implementing both an internal API the MLJ model interface. EvoTreeCount is used to perform Poisson probabilistic regression on count target.

# Hyper-parameters

  * `early_stopping_rounds::Integer`: number of consecutive rounds without metric improvement after which fitting in stopped.
  * `nrounds=100`:           Number of rounds. It corresponds to the number of trees that will be sequentially stacked. Must be >= 1.
  * `eta=0.1`:              Learning rate. Each tree raw predictions are scaled by `eta` prior to be added to the stack of predictions. Must be > 0. A lower `eta` results in slower learning, requiring a higher `nrounds` but typically improves model performance.
  * `L2::T=0.0`:            L2 regularization factor on aggregate gain. Must be >= 0. Higher L2 can result in a more robust model.
  * `lambda::T=0.0`:        L2 regularization factor on individual gain. Must be >= 0. Higher lambda can result in a more robust model.
  * `gamma::T=0.0`:         Minimum gain imprvement needed to perform a node split. Higher gamma can result in a more robust model.
  * `max_depth=6`:          Maximum depth of a tree. Must be >= 1. A tree of depth 1 is made of a single prediction leaf. A complete tree of depth N contains `2^(N - 1)` terminal leaves and `2^(N - 1) - 1` split nodes. Compute cost is proportional to 2^max_depth. Typical optimal values are in the 3 to 9 range.
  * `min_weight=1.0`:       Minimum weight needed in a node to perform a split. Matches the number of observations by default or the sum of weights as provided by the `weights` vector. Must be > 0.
  * `rowsample=1.0`:        Proportion of rows that are sampled at each iteration to build the tree. Should be `]0, 1]`.
  * `colsample=1.0`:        Proportion of columns / features that are sampled at each iteration to build the tree. Should be `]0, 1]`.
  * `nbins=64`:             Number of bins into which each feature is quantized. Buckets are defined based on quantiles, hence resulting in equal weight bins. Should be between 2 and 255.
  * `monotone_constraints=Dict{Int, Int}()`: Specify monotonic constraints using a dict where the key is the feature index and the value the applicable constraint (-1=decreasing, 0=none, 1=increasing).
  * `tree_type=:binary`    Tree structure to be used. One of:

      * `:binary`:       Each node of a tree is grown independently. Tree are built depthwise until max depth is reach or if min weight or gain (see `gamma`) stops further node splits.
      * `:oblivious`:    A common splitting condition is imposed to all nodes of a given depth.
  * `rng=123`:              Either an integer used as a seed to the random number generator or an actual random number generator (`::Random.AbstractRNG`).
  * `device=:cpu`: Hardware device to use for computations. Can be either `:cpu` or `:gpu`.

# Internal API

Do `config = EvoTreeCount()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in EvoTreeCount(max_depth=...).

## Training model

A model is built using [`fit_evotree`](@ref):

```julia
model = fit_evotree(config; x_train, y_train, kwargs...)
```

## Inference

Predictions are obtained using [`predict`](@ref) which returns a `Vector` of length `nobs`:

```julia
EvoTrees.predict(model, X)
```

Alternatively, models act as a functor, returning predictions when called as a function with features as argument:

```julia
model(X)
```

# MLJ

From MLJ, the type can be imported using:

```julia
EvoTreeCount = @load EvoTreeCount pkg=EvoTrees
```

Do `model = EvoTreeCount()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `EvoTreeCount(loss=...)`.

## Training data

In MLJ or MLJBase, bind an instance `model` to data with     mach = machine(model, X, y) where

  * `X`: any table of input features (eg, a `DataFrame`) whose columns each have one of the following element scitypes: `Continuous`, `Count`, or `<:OrderedFactor`; check column scitypes with `schema(X)`
  * `y`: is the target, which can be any `AbstractVector` whose element scitype is `<:Count`; check the scitype with `scitype(y)`

Train the machine using `fit!(mach, rows=...)`.

# Operations

  * `predict(mach, Xnew)`: returns a vector of Poisson distributions given features `Xnew` having the same scitype as `X` above. Predictions are probabilistic.

Specific metrics can also be predicted using:

  * `predict_mean(mach, Xnew)`
  * `predict_mode(mach, Xnew)`
  * `predict_median(mach, Xnew)`

## Fitted parameters

The fields of `fitted_params(mach)` are:

  * `:fitresult`: The `GBTree` object returned by EvoTrees.jl fitting algorithm.

## Report

The fields of `report(mach)` are:

  * `:features`: The names of the features encountered in training.

# Examples

```
# Internal API
using EvoTrees
config = EvoTreeCount(max_depth=5, nbins=32, nrounds=100)
nobs, nfeats = 1_000, 5
x_train, y_train = randn(nobs, nfeats), rand(0:2, nobs)
model = fit_evotree(config; x_train, y_train)
preds = EvoTrees.predict(model, x_train)
```

```
using MLJ
EvoTreeCount = @load EvoTreeCount pkg=EvoTrees
model = EvoTreeCount(max_depth=5, nbins=32, nrounds=100)
nobs, nfeats = 1_000, 5
X, y = randn(nobs, nfeats), rand(0:2, nobs)
mach = machine(model, X, y) |> fit!
preds = predict(mach, X)
preds = predict_mean(mach, X)
preds = predict_mode(mach, X)
preds = predict_median(mach, X)

```

See also [EvoTrees.jl](https://github.com/Evovest/EvoTrees.jl).
