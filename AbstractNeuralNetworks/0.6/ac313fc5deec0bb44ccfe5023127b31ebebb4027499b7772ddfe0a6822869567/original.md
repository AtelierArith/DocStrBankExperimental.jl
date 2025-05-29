```
NetworkLoss
```

An abstract type for all the neural network losses.  If you want to implement `CustomLoss <: NetworkLoss` you need to define a functor:

```julia
(loss::CustomLoss)(model, ps, input, output)
```

where `model` is an instance of an `AbstractExplicitLayer` or a `Chain` and `ps` the parameters.

See [`FeedForwardLoss`](@ref), `GeometricMachineLearning.TransformerLoss`, `GeometricMachineLearning.AutoEncoderLoss` and `GeometricMachineLearning.ReducedLoss` for examples.
