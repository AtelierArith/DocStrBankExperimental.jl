```
ImageClassifier
```

A model type for constructing a image classifier, based on [MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
ImageClassifier = @load ImageClassifier pkg=MLJFlux
```

Do `model = ImageClassifier()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `ImageClassifier(builder=...)`.

`ImageClassifier` classifies images using a neural network adapted to the type of images provided (color or gray scale). Predictions are probabilistic. Users provide a recipe for constructing the network, based on properties of the image encountered, by specifying an appropriate `builder`. See MLJFlux documentation for more on builders.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any `AbstractVector` of images with `ColorImage` or `GrayImage` scitype; check  the scitype with `scitype(X)` and refer to ScientificTypes.jl documentation on coercing  typical image formats into an appropriate type.
  * `y` is the target, which can be any `AbstractVector` whose element  scitype is `Multiclass`; check the scitype with `scitype(y)`.

Train the machine with `fit!(mach, rows=...)`.

# Hyper-parameters

  * `builder`: An MLJFlux builder that constructs the neural network.  The fallback builds a  depth-16 VGG architecture adapted to the image size and number of target classes, with  no batch normalization; see the Metalhead.jl documentation for details. See the example  below for a user-specified builder. A convenience macro `@builder` is also  available. See also `finaliser` below.
  * `optimiser::Optimisers.Adam()`: An Optimisers.jl optimiser. The optimiser performs the updating of the weights of the network. To choose a learning rate (the update rate of the optimizer), a good rule of thumb is to start out at `10e-3`, and tune using powers of `10` between `1` and `1e-7`.
  * `loss=Flux.crossentropy`: The loss function which the network will optimize. Should be a function which can be called in the form `loss(yhat, y)`.  Possible loss functions are listed in [the Flux loss function documentation](https://fluxml.ai/Flux.jl/stable/models/losses/). For a classification task, the most natural loss functions are:

      * `Flux.crossentropy`: Standard multiclass classification loss, also known as the log loss.
      * `Flux.logitcrossentopy`: Mathematically equal to crossentropy, but numerically more stable than finalising the outputs with `softmax` and then calculating crossentropy. You will need to specify `finaliser=identity` to remove MLJFlux's default softmax finaliser, and understand that the output of `predict` is then unnormalized (no longer probabilistic).
      * `Flux.tversky_loss`: Used with imbalanced data to give more weight to false negatives.
      * `Flux.focal_loss`: Used with highly imbalanced data. Weights harder examples more than easier examples.

    Currently MLJ measures are not supported values of `loss`.
  * `epochs::Int=10`: The duration of training, in epochs. Typically, one epoch represents one pass through the complete the training dataset.
  * `batch_size::int=1`: the batch size to be used for training, representing the number of samples per update of the network weights. Typically, batch size is between 8 and

    512. Increassing batch size may accelerate training if `acceleration=CUDALibs()` and a

    GPU is available.
  * `lambda::Float64=0`: The strength of the weight regularization penalty. Can be any value in the range `[0, ∞)`. Note the history reports unpenalized losses.
  * `alpha::Float64=0`: The L2/L1 mix of regularization, in the range `[0, 1]`. A value of 0 represents L2 regularization, and a value of 1 represents L1 regularization.
  * `rng::Union{AbstractRNG, Int64}`: The random number generator or seed used during training. The default is `Random.default_rng()`.
  * `optimizer_changes_trigger_retraining::Bool=false`: Defines what happens when re-fitting a machine if the associated optimiser has changed. If `true`, the associated machine will retrain from scratch on `fit!` call, otherwise it will not.
  * `acceleration::AbstractResource=CPU1()`: Defines on what hardware training is done. For Training on GPU, use `CUDALibs()`.
  * `finaliser=Flux.softmax`: The final activation function of the neural network (applied after the network defined by `builder`). Defaults to `Flux.softmax`.

# Operations

  * `predict(mach, Xnew)`: return predictions of the target given new features `Xnew`, which should have the same scitype as `X` above. Predictions are probabilistic but uncalibrated.
  * `predict_mode(mach, Xnew)`: Return the modes of the probabilistic predictions returned above.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `chain`: The trained "chain" (Flux.jl model), namely the series of layers,  functions, and activations  which make up the neural network. This includes  the final layer specified by `finaliser` (eg, `softmax`).

# Report

The fields of `report(mach)` are:

  * `training_losses`: A vector of training losses (penalised if `lambda != 0`) in  historical order, of length `epochs + 1`.  The first element is the pre-training loss.

# Examples

In this example we use MLJFlux and a custom builder to classify the MNIST image dataset.

```julia
using MLJ
using Flux
import MLJFlux
import Optimisers
import MLJIteration # for `skip` control
```

First we want to download the MNIST dataset, and unpack into images and labels:

```julia
import MLDatasets: MNIST
data = MNIST(split=:train)
images, labels = data.features, data.targets
```

In MLJ, integers cannot be used for encoding categorical data, so we must coerce them into the `Multiclass` scitype:

```julia
labels = coerce(labels, Multiclass);
```

Above `images` is a single array but MLJFlux requires the images to be a vector of individual image arrays:

```
images = coerce(images, GrayImage);
images[1]
```

We start by defining a suitable `builder` object. This is a recipe for building the neural network. Our builder will work for images of any (constant) size, whether they be color or black and white (ie, single or multi-channel).  The architecture always consists of six alternating convolution and max-pool layers, and a final dense layer; the filter size and the number of channels after each convolution layer is customizable.

```julia
import MLJFlux

struct MyConvBuilder
    filter_size::Int
    channels1::Int
    channels2::Int
    channels3::Int
end

make2d(x::AbstractArray) = reshape(x, :, size(x)[end])

function MLJFlux.build(b::MyConvBuilder, rng, n_in, n_out, n_channels)
    k, c1, c2, c3 = b.filter_size, b.channels1, b.channels2, b.channels3
    mod(k, 2) == 1 || error("`filter_size` must be odd. ")
    p = div(k - 1, 2) # padding to preserve image size
    init = Flux.glorot_uniform(rng)
    front = Chain(
        Conv((k, k), n_channels => c1, pad=(p, p), relu, init=init),
        MaxPool((2, 2)),
        Conv((k, k), c1 => c2, pad=(p, p), relu, init=init),
        MaxPool((2, 2)),
        Conv((k, k), c2 => c3, pad=(p, p), relu, init=init),
        MaxPool((2 ,2)),
        make2d)
    d = Flux.outputsize(front, (n_in..., n_channels, 1)) |> first
    return Chain(front, Dense(d, n_out, init=init))
end
```

It is important to note that in our `build` function, there is no final `softmax`. This is applied by default in all MLJFlux classifiers (override this using the `finaliser` hyperparameter).

Now that our builder is defined, we can instantiate the actual MLJFlux model. If you have a GPU, you can substitute in `acceleration=CUDALibs()` below to speed up training.

```julia
ImageClassifier = @load ImageClassifier pkg=MLJFlux
clf = ImageClassifier(builder=MyConvBuilder(3, 16, 32, 32),
                      batch_size=50,
                      epochs=10,
                      rng=123)
```

You can add Flux options such as `optimiser` and `loss` in the snippet above. Currently, `loss` must be a flux-compatible loss, and not an MLJ measure.

Next, we can bind the model with the data in a machine, and train using the first 500 images:

```julia
mach = machine(clf, images, labels);
fit!(mach, rows=1:500, verbosity=2);
report(mach)
chain = fitted_params(mach)
Flux.params(chain)[2]
```

We can tack on 20 more epochs by modifying the `epochs` field, and iteratively fit some more:

```julia
clf.epochs = clf.epochs + 20
fit!(mach, rows=1:500, verbosity=2);
```

We can also make predictions and calculate an out-of-sample loss estimate, using any MLJ measure (loss/score):

```julia
predicted_labels = predict(mach, rows=501:1000);
cross_entropy(predicted_labels, labels[501:1000])
```

The preceding `fit!`/`predict`/evaluate workflow can be alternatively executed as follows:

```julia
evaluate!(mach,
          resampling=Holdout(fraction_train=0.5),
          measure=cross_entropy,
          rows=1:1000,
          verbosity=0)
```

See also [`NeuralNetworkClassifier`](@ref).
