```
abstract type FluxModule end
```

An abstract type for Flux models. A `FluxModule` helps orgainising you code and provides a standard interface for training.

A `FluxModule` comes with the functionality provided by `Flux.@layer`  (pretty printing, etc...) and the ability to interact with  [`Trainer`](@ref) and `Optimisers.jl`.

You can change the trainables by implementing `Optimisers.trainables`.

Types subtyping from `FluxModule` have to implement the following methods  in order to interact with a [`Trainer`](@ref).

# Required methods

  * [`configure_optimisers`](@ref)`(model, trainer)`.
  * [`train_step`](@ref)`(model, trainer, batch, [batch_idx])`.

# Optional Methods

  * [`val_step`](@ref)`(model, trainer, batch, [batch_idx])`.
  * [`test_step`](@ref)`(model, trainer, batch, [batch_idx])`.
  * generic [hooks](@ref Hooks).

# Examples

```julia
using Flux, Tsunami, Optimisers

# Define a Multilayer Perceptron implementing the FluxModule interface

struct Model <: FluxModule
    net
end

function Model()
    net = Chain(Dense(4 => 32, relu), Dense(32 => 2))
    return Model(net)
end

(model::Model)(x) = model.net(x)

function Tsunami.train_step(model::Model, trainer, batch)
    x, y = batch
    y_hat = model(x)
    loss = Flux.Losses.mse(y_hat, y)
    return loss
end

function Tsunami.configure_optimisers(model::Model, trainer)
    return Optimisers.setup(Optimisers.Adam(1f-3), model)
end

# Prepare the dataset and the DataLoader
X, Y = rand(4, 100), rand(2, 100)
train_dataloader = Flux.DataLoader((X, Y), batchsize=10)

# Create and Train the model
model = Model()
trainer = Trainer(max_epochs=10)
Tsunami.fit!(model, trainer, train_dataloader)
```
