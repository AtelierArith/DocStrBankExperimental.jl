```
Chain
```

A chain is a sequence of layers.

A `Chain` can be initialized by passing an arbitrary number of layers

```
Chain(layers...)
```

or a neural network architecture together with a backend and a parameter type:

```
Chain(::Architecture, ::NeuralNetworkBackend, ::Type; kwargs...)
Chain(::Architecture, ::Type; kwargs...)
```

If the backend is omitted, the default backend `CPU()` is chosen. The keyword arguments will be passed to the `initialparameters` method of each layer.
