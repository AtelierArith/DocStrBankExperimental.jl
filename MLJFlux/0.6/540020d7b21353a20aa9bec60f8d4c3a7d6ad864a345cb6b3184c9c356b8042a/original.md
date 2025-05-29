```
NeuralNetworkRegressor
```

A model type for constructing a neural network regressor, based on [MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
NeuralNetworkRegressor = @load NeuralNetworkRegressor pkg=MLJFlux
```

Do `model = NeuralNetworkRegressor()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `NeuralNetworkRegressor(builder=...)`.

`NeuralNetworkRegressor` is for training a data-dependent Flux.jl neural network to predict a `Continuous` target, given a table of `Continuous` features. Users provide a recipe for constructing the network, based on properties of the data that is encountered, by specifying an appropriate `builder`. See MLJFlux documentation for more on builders.

In addition to features with `Continuous` scientific element type, this model supports categorical features in the input table. If present, such features are embedded into dense vectors by the use of an additional `EntityEmbedderLayer` layer after the input, as described in Entity Embeddings of Categorical Variables by Cheng Guo, Felix Berkhahn arXiv, 2016.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` provides input features and is either: (i) a `Matrix` with `Continuous` element scitype (typically `Float32`); or (ii) a table of input features (eg, a `DataFrame`) whose columns have `Continuous`, `Multiclass` or `OrderedFactor` element scitype; check column scitypes with `schema(X)`.  If any `Multiclass` or `OrderedFactor` features appear, the constructed network will use an `EntityEmbedderLayer` layer to transform them into dense vectors. If `X` is a `Matrix`, it is assumed that columns correspond to features and rows corresponding to observations.

  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Continuous`; check the scitype with `scitype(y)`

Train the machine with `fit!(mach, rows=...)`.

# Hyper-parameters

  * `builder=MLJFlux.Linear(σ=Flux.relu)`: An MLJFlux builder that constructs a neural  network. Possible `builders` include: `MLJFlux.Linear`, `MLJFlux.Short`, and  `MLJFlux.MLP`. See MLJFlux documentation for more on builders, and the example below  for using the `@builder` convenience macro.
  * `optimiser::Optimisers.Adam()`: An Optimisers.jl optimiser. The optimiser performs the updating of the weights of the network. To choose a learning rate (the update rate of the optimizer), a good rule of thumb is to start out at `10e-3`, and tune using powers of `10` between `1` and `1e-7`.
  * `loss=Flux.mse`: The loss function which the network will optimize. Should be a function which can be called in the form `loss(yhat, y)`.  Possible loss functions are listed in [the Flux loss function documentation](https://fluxml.ai/Flux.jl/stable/models/losses/). For a regression task, natural loss functions are:

      * `Flux.mse`
      * `Flux.mae`
      * `Flux.msle`
      * `Flux.huber_loss`

    Currently MLJ measures are not supported as loss functions here.
  * `epochs::Int=10`: The duration of training, in epochs. Typically, one epoch represents one pass through the complete the training dataset.
  * `batch_size::int=1`: the batch size to be used for training, representing the number of samples per update of the network weights. Typically, batch size is between `8` and `512`. Increasing batch size may accelerate training if `acceleration=CUDALibs()` and a GPU is available.
  * `lambda::Float64=0`: The strength of the weight regularization penalty. Can be any value in the range `[0, ∞)`. Note the history reports unpenalized losses.
  * `alpha::Float64=0`: The L2/L1 mix of regularization, in the range `[0, 1]`. A value of 0 represents L2 regularization, and a value of 1 represents L1 regularization.
  * `rng::Union{AbstractRNG, Int64}`: The random number generator or seed used during training. The default is `Random.default_rng()`.
  * `optimizer_changes_trigger_retraining::Bool=false`: Defines what happens when re-fitting a machine if the associated optimiser has changed. If `true`, the associated machine will retrain from scratch on `fit!` call, otherwise it will not.
  * `acceleration::AbstractResource=CPU1()`: Defines on what hardware training is done. For Training on GPU, use `CUDALibs()`.
  * `embedding_dims`: a `Dict` whose keys are names of categorical features, given as symbols, and whose values are numbers representing the desired dimensionality of the entity embeddings of such features: an integer value of `7`, say, sets the embedding dimensionality to `7`; a float value of `0.5`, say, sets the embedding dimensionality to `ceil(0.5 * c)`, where `c` is the number of feature levels.  Unspecified feature dimensionality defaults to `min(c - 1, 10)`.

# Operations

  * `predict(mach, Xnew)`: return predictions of the target given new features `Xnew`, which should have the same scitype as `X` above.
  * `transform(mach, Xnew)`: Assuming `Xnew` has the same schema as `X`, transform the categorical features of `Xnew` into dense `Continuous` vectors using the `MLJFlux.EntityEmbedderLayer` layer present in the network. Does nothing in case the model was trained on an input `X` that lacks categorical features.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `chain`: The trained "chain" (Flux.jl model), namely the series of layers, functions,  and activations which make up the neural network.

# Report

The fields of `report(mach)` are:

  * `training_losses`: A vector of training losses (penalized if `lambda != 0`) in  historical order, of length `epochs + 1`.  The first element is the pre-training loss.

# Examples

In this example we build a regression model for the Boston house price dataset.

```julia
using MLJ
import MLJFlux
using Flux
import Optimisers
```

First, we load in the data: The `:MEDV` column becomes the target vector `y`, and all remaining columns go into a table `X`, with the exception of `:CHAS`:

```julia
data = OpenML.load(531); # Loads from https://www.openml.org/d/531
y, X = unpack(data, ==(:MEDV), !=(:CHAS); rng=123);

scitype(y)
schema(X)
```

Since MLJFlux models do not handle ordered factors, we'll treat `:RAD` as `Continuous`:

```julia
X = coerce(X, :RAD=>Continuous)
```

Splitting off a test set:

```julia
(X, Xtest), (y, ytest) = partition((X, y), 0.7, multi=true);
```

Next, we can define a `builder`, making use of a convenience macro to do so.  In the following `@builder` call, `n_in` is a proxy for the number input features (which will be known at `fit!` time) and `rng` is a proxy for a RNG (which will be passed from the `rng` field of `model` defined below). We also have the parameter `n_out` which is the number of output features. As we are doing single target regression, the value passed will always be `1`, but the builder we define will also work for [`MultitargetNeuralNetworkRegressor`](@ref).

```julia
builder = MLJFlux.@builder begin
    init=Flux.glorot_uniform(rng)
    Chain(
        Dense(n_in, 64, relu, init=init),
        Dense(64, 32, relu, init=init),
        Dense(32, n_out, init=init),
    )
end
```

Instantiating a model:

```julia
NeuralNetworkRegressor = @load NeuralNetworkRegressor pkg=MLJFlux
model = NeuralNetworkRegressor(
    builder=builder,
    rng=123,
    epochs=20
)
```

We arrange for standardization of the the target by wrapping our model in `TransformedTargetModel`, and standardization of the features by inserting the wrapped model in a pipeline:

```julia
pipe = Standardizer |> TransformedTargetModel(model, transformer=Standardizer)
```

If we fit with a high verbosity (>1), we will see the losses during training. We can also see the losses in the output of `report(mach)`.

```julia
mach = machine(pipe, X, y)
fit!(mach, verbosity=2)

# first element initial loss, 2:end per epoch training losses
report(mach).transformed_target_model_deterministic.model.training_losses
```

## Experimenting with learning rate

We can visually compare how the learning rate affects the predictions:

```julia
using Plots

rates = rates = [5e-5, 1e-4, 0.005, 0.001, 0.05]
plt=plot()

foreach(rates) do η
  pipe.transformed_target_model_deterministic.model.optimiser = Optimisers.Adam(η)
  fit!(mach, force=true, verbosity=0)
  losses =
      report(mach).transformed_target_model_deterministic.model.training_losses[3:end]
  plot!(1:length(losses), losses, label=η)
end

plt

pipe.transformed_target_model_deterministic.model.optimiser.eta = Optimisers.Adam(0.0001)
```

With the learning rate fixed, we compute a CV estimate of the performance (using all data bound to `mach`) and compare this with performance on the test set:

```julia
# CV estimate, based on `(X, y)`:
evaluate!(mach, resampling=CV(nfolds=5), measure=l2)

# loss for `(Xtest, test)`:
fit!(mach) # train on `(X, y)`
yhat = predict(mach, Xtest)
l2(yhat, ytest)
```

These losses, for the pipeline model, refer to the target on the original, unstandardized, scale.

For implementing stopping criterion and other iteration controls, refer to examples linked from the MLJFlux documentation.

See also [`MultitargetNeuralNetworkRegressor`](@ref)
