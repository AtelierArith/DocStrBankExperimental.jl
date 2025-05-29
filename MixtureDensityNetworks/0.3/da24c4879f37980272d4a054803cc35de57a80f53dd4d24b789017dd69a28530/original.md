```
MDN
```

A model type for constructing a Mixture Density Network, based on [MixtureDensityNetworks.jl](https://github.com/JoshuaBillson/MixtureDensityNetworks.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
MDN = @load MDN pkg=MixtureDensityNetworks
```

Do `model = MDN()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `MDN(mixtures=...)`.

A neural network which parameterizes a Gaussian Mixture Model (GMM)  distributed over the target varible `y` conditioned on the features `X`.

# Training Data

In MLJ or MLJBase, bind an `MDN` instance `model` to data with     mach = machine(model, X, y) where

  * `X`: any table of input features (eg, a `DataFrame`) whose columns belong to the `Continuous` scitypes`.
  * `y`: the target, which can be any `AbstractVector` whose element scitype is `Continuous`.

# Hyperparameters

  * `mixtures=5`: number of Gaussian mixtures in the predicted distribution
  * `layers=[128,]`: hidden layer topology, starting from the first hidden layer
  * `η=1e-3`: learning rate used for the optimizer
  * `epochs=1`: number of epochs to train the model
  * `batchsize=32`: batch size used during training

# Operations

  * `predict(mach, Xnew)`: return the distributions over the target conditioned on the new features `Xnew` having the same scitype as `X` above.
  * `predict_mode(mach, Xnew)`: return the largest modes of the distributions over targets   conditioned on the new features `Xnew` having the same scitype as `X` above.
  * `predict_mean(mach, Xnew)`: return the means of the distributions over targets   conditioned on the new features `Xnew` having the same scitype as `X` above.
  * `predict_median(mach, Xnew)`: return the medians of the distributions over targets   conditioned on the new features `Xnew` having the same scitype as `X` above.

# Fitted Parameters

The fields of `fitted_params(mach)` are:

  * `fitresult`: the trained mixture density model, compatible with the Flux ecosystem.

# Report

  * `learning_curve`: the average training loss for each epoch.
  * `best_epoch`: the epoch (starting from 1) with the lowest training loss.
  * `best_loss`: the best (lowest) loss encountered durind training. Corresponds  to the average loss of the best epoch.

# Accessor Functions

  * `training_losses(mach)` returns the learning curve as a vector of average  training losses for each epoch.

# Examples

```
using MLJ
MDN = @load MDN pkg=MixtureDensityNetworks
mdn = MDN(mixtures=12, epochs=100, layers=[512, 256, 128])
X, y = make_regression(100, 1) # synthetic data
mach = machine(mdn, X, y) |> fit!
Xnew, _ = make_regression(3, 1)
ŷ = predict(mach, Xnew) # new predictions
report(mach).best_epoch # best epoch encountered during training 
report(mach).best_loss # best loss encountered during training 
training_losses(mach) # learning curve
```
