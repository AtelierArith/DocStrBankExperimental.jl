```
NeuralNetworkBinaryClassifier
```

A model type for constructing a neural network binary classifier, based on [MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
NeuralNetworkBinaryClassifier = @load NeuralNetworkBinaryClassifier pkg=MLJFlux
```

Do `model = NeuralNetworkBinaryClassifier()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `NeuralNetworkBinaryClassifier(builder=...)`.

`NeuralNetworkBinaryClassifier` is for training a data-dependent Flux.jl neural network for making probabilistic predictions of a binary (`Multiclass{2}` or `OrderedFactor{2}`) target, given a table of `Continuous` features. Users provide a recipe for constructing  the network, based on properties of the data that is encountered, by specifying  an appropriate `builder`. See MLJFlux documentation for more on builders.

In addition to features with `Continuous` scientific element type, this model supports categorical features in the input table. If present, such features are embedded into dense vectors by the use of an additional `EntityEmbedderLayer` layer after the input, as described in Entity Embeddings of Categorical Variables by Cheng Guo, Felix Berkhahn arXiv, 2016.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` provides input features and is either: (i) a `Matrix` with `Continuous` element scitype (typically `Float32`); or (ii) a table of input features (eg, a `DataFrame`) whose columns have `Continuous`, `Multiclass` or `OrderedFactor` element scitype; check column scitypes with `schema(X)`.  If any `Multiclass` or `OrderedFactor` features appear, the constructed network will use an `EntityEmbedderLayer` layer to transform them into dense vectors. If `X` is a `Matrix`, it is assumed that columns correspond to features and rows corresponding to observations.

  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Multiclass{2}` or `OrderedFactor{2}`; check the scitype with `scitype(y)`

Train the machine with `fit!(mach, rows=...)`.

# Hyper-parameters

  * `builder=MLJFlux.Short()`: An MLJFlux builder that constructs a neural network. Possible  `builders` include: `MLJFlux.Linear`, `MLJFlux.Short`, and `MLJFlux.MLP`. See  MLJFlux.jl documentation for examples of user-defined builders. See also `finaliser`  below.
  * `optimiser::Flux.Adam()`: A `Flux.Optimise` optimiser. The optimiser performs the updating of the weights of the network. For further reference, see [the Flux optimiser documentation](https://fluxml.ai/Flux.jl/stable/training/optimisers/). To choose a learning rate (the update rate of the optimizer), a good rule of thumb is to start out at `10e-3`, and tune using powers of `10` between `1` and `1e-7`.
  * `loss=Flux.binarycrossentropy`: The loss function which the network will optimize. Should be a function which can be called in the form `loss(yhat, y)`.  Possible loss functions are listed in [the Flux loss function documentation](https://fluxml.ai/Flux.jl/stable/models/losses/). For a classification task, the most natural loss functions are:

      * `Flux.binarycrossentropy`: Standard binary classification loss, also known as the log loss.
      * `Flux.logitbinarycrossentropy`: Mathematically equal to crossentropy, but numerically more stable than finalising the outputs with `σ` and then calculating crossentropy. You will need to specify `finaliser=identity` to remove MLJFlux's default sigmoid finaliser, and understand that the output of `predict` is then unnormalized (no longer probabilistic).
      * `Flux.tversky_loss`: Used with imbalanced data to give more weight to false negatives.
      * `Flux.binary_focal_loss`: Used with highly imbalanced data. Weights harder examples more than easier examples.

    Currently MLJ measures are not supported values of `loss`.
  * `epochs::Int=10`: The duration of training, in epochs. Typically, one epoch represents one pass through the complete the training dataset.
  * `batch_size::int=1`: the batch size to be used for training, representing the number of samples per update of the network weights. Typically, batch size is between `8` and `512`. Increassing batch size may accelerate training if `acceleration=CUDALibs()` and a GPU is available.
  * `lambda::Float64=0`: The strength of the weight regularization penalty. Can be any value in the range `[0, ∞)`.
  * `alpha::Float64=0`: The L2/L1 mix of regularization, in the range `[0, 1]`. A value of 0 represents L2 regularization, and a value of 1 represents L1 regularization.
  * `rng::Union{AbstractRNG, Int64}`: The random number generator or seed used during training.
  * `optimizer_changes_trigger_retraining::Bool=false`: Defines what happens when re-fitting a machine if the associated optimiser has changed. If `true`, the associated machine will retrain from scratch on `fit!` call, otherwise it will not.
  * `acceleration::AbstractResource=CPU1()`: Defines on what hardware training is done. For Training on GPU, use `CUDALibs()`.
  * `finaliser=Flux.σ`: The final activation function of the neural network (applied after the network defined by `builder`). Defaults to `Flux.σ`.
  * `embedding_dims`: a `Dict` whose keys are names of categorical features, given as symbols, and whose values are numbers representing the desired dimensionality of the entity embeddings of such features: an integer value of `7`, say, sets the embedding dimensionality to `7`; a float value of `0.5`, say, sets the embedding dimensionality to `ceil(0.5 * c)`, where `c` is the number of feature levels.  Unspecified feature dimensionality defaults to `min(c - 1, 10)`.

# Operations

  * `predict(mach, Xnew)`: return predictions of the target given new features `Xnew`, which should have the same scitype as `X` above. Predictions are probabilistic but uncalibrated.
  * `predict_mode(mach, Xnew)`: Return the modes of the probabilistic predictions returned above.
  * `transform(mach, Xnew)`: Assuming `Xnew` has the same schema as `X`, transform the categorical features of `Xnew` into dense `Continuous` vectors using the `MLJFlux.EntityEmbedderLayer` layer present in the network. Does nothing in case the model was trained on an input `X` that lacks categorical features.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `chain`: The trained "chain" (Flux.jl model), namely the series of layers,  functions, and activations which make up the neural network. This includes  the final layer specified by `finaliser` (eg, `softmax`).

# Report

The fields of `report(mach)` are:

  * `training_losses`: A vector of training losses (penalised if `lambda != 0`) in  historical order, of length `epochs + 1`.  The first element is the pre-training loss.

# Examples

In this example we build a classification model using the Iris dataset. This is a very basic example, using a default builder and no standardization.  For a more advanced illustration, see [`NeuralNetworkRegressor`](@ref) or [`ImageClassifier`](@ref), and examples in the MLJFlux.jl documentation.

```julia
using MLJ, Flux
import Optimisers
import RDatasets
```

First, we can load the data:

```julia
mtcars = RDatasets.dataset("datasets", "mtcars");
y, X = unpack(mtcars, ==(:VS), in([:MPG, :Cyl, :Disp, :HP, :WT, :QSec]));
```

Note that `y` is a vector and `X` a table.

```julia
y = categorical(y) # classifier takes catogorical input
X_f32 = Float32.(X) # To match floating point type of the neural network layers
NeuralNetworkBinaryClassifier = @load NeuralNetworkBinaryClassifier pkg=MLJFlux
bclf = NeuralNetworkBinaryClassifier()
```

Next, we can train the model:

```julia
mach = machine(bclf, X_f32, y)
fit!(mach)
```

We can train the model in an incremental fashion, altering the learning rate as we go, provided `optimizer_changes_trigger_retraining` is `false` (the default). Here, we also change the number of (total) iterations:

```julia-repl
julia> bclf.optimiser
Adam(0.001, (0.9, 0.999), 1.0e-8)
```

```julia
bclf.optimiser = Optimisers.Adam(eta = bclf.optimiser.eta * 2)
bclf.epochs = bclf.epochs + 5

fit!(mach, verbosity=2) # trains 5 more epochs
```

We can inspect the mean training loss using the `cross_entropy` function:

```julia
training_loss = cross_entropy(predict(mach, X_f32), y)
```

And we can access the Flux chain (model) using `fitted_params`:

```julia
chain = fitted_params(mach).chain
```

Finally, we can see how the out-of-sample performance changes over time, using MLJ's `learning_curve` function:

```julia
r = range(bclf, :epochs, lower=1, upper=200, scale=:log10)
curve = learning_curve(
    bclf,
    X_f32,
    y,
    range=r,
    resampling=Holdout(fraction_train=0.7),
    measure=cross_entropy,
)
using Plots
plot(
   curve.parameter_values,
   curve.measurements,
   xlab=curve.parameter_name,
   xscale=curve.parameter_scale,
   ylab = "Cross Entropy",
)

```

See also [`ImageClassifier`](@ref).
