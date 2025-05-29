```
NeuroTreeClassifier(; kwargs...)
```

A model type for constructing a NeuroTreeClassifier, based on [NeuroTreeModels.jl](https://github.com/Evovest/NeuroTreeModels.jl), and implementing both an internal API and the MLJ model interface.

# Hyper-parameters

  * `nrounds=100`:             Max number of rounds (epochs).
  * `lr=1.0f-2`:              Learning rate. Must be > 0. A lower `eta` results in slower learning, typically requiring a higher `nrounds`.
  * `wd=0.f0`:                Weight decay applied to the gradients by the optimizer.
  * `batchsize=2048`:         Batch size.
  * `actA=:tanh`:             Activation function applied to each of input variable for determination of split node weight. Can be one of:

      * `:tanh`
      * `:identity`
  * `depth=6`:            Depth of a tree. Must be >= 1. A tree of depth 1 has 2 prediction leaf nodes. A complete tree of depth N contains `2^N` terminal leaves and `2^N - 1` split nodes. Compute cost is proportional to `2^depth`. Typical optimal values are in the 3 to 5 range.
  * `ntrees=64`:              Number of trees (per stack).
  * `hidden_size=16`:         Size of hidden layers. Applicable only when `stack_size` > 1.
  * `stack_size=1`:           Number of stacked NeuroTree blocks.
  * `scaler=true`:            Whether a learnable scaling factor, prior to the sigmoid activation, should be used. Otherwise a fixed scaling of 1.0 is used if `scaler=false`.
  * `init_scale=0.1`:         Scaling factor applied to the predictions weights. Values in the range `]0, 1]` should result in best convergence.
  * `MLE_tree_split=false`:   Whether independent models are buillt for each of the 2 parameters (mu, sigma) of the the `gaussian_mle` loss.
  * `rng=123`:                Either an integer used as a seed to the random number generator or an actual random number generator (`::Random.AbstractRNG`).
  * `device=:cpu`:            Device on which to perform the computation, either `:cpu` or `:gpu`
  * `gpuID=0`:                GPU device to use, only relveant if `device = :gpu`

# Internal API

Do `config = NeuroTreeClassifier()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `NeuroTreeClassifier(depth=5, ...)`.

## Training model

A model is trained using [`fit`](@ref):

```julia
m = fit(config, dtrain; feature_names, target_name, kwargs...)
```

## Inference

Models act as a functor. returning predictions when called as a function with features as argument:

```julia
m(data)
```

# MLJ Interface

From MLJ, the type can be imported using:

```julia
NeuroTreeClassifier = @load NeuroTreeClassifier pkg=NeuroTreeModels
```

Do `model = NeuroTreeClassifier()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `NeuroTreeClassifier(loss=...)`.

## Training model

In MLJ or MLJBase, bind an instance `model` to data with     `mach = machine(model, X, y)` where

  * `X`: any table of input features (eg, a `DataFrame`) whose columns each have one of the following element scitypes: `Continuous`, `Count`, or `<:OrderedFactor`; check column scitypes with `schema(X)`
  * `y`: is the target, which can be any `AbstractVector` whose element scitype is `<:Finite`; check the scitype with `scitype(y)`

Train the machine using `fit!(mach, rows=...)`.

## Operations

  * `predict(mach, Xnew)`: return predictions of the target given features `Xnew` having the same scitype as `X` above.

## Fitted parameters

The fields of `fitted_params(mach)` are:

  * `:fitresult`: The `NeuroTreeModel` object.

## Report

The fields of `report(mach)` are:

  * `:features`: The names of the features encountered in training.

# Examples

## Internal API

```julia
using NeuroTreeModels, DataFrames, CategoricalArrays, Random 
config = NeuroTreeClassifier(depth=5, nrounds=10)
nobs, nfeats = 1_000, 5
dtrain = DataFrame(randn(nobs, nfeats), :auto)
dtrain.y = categorical(rand(1:2, nobs))
feature_names, target_name = names(dtrain, r"x"), "y"
m = fit(config, dtrain; feature_names, target_name)
p = m(dtrain)
```

## MLJ Interface

```julia
using MLJBase, NeuroTreeModels
m = NeuroTreeClassifier(depth=5, nrounds=10)
X, y = @load_crabs
mach = machine(m, X, y) |> fit!
p = predict(mach, X)
```
