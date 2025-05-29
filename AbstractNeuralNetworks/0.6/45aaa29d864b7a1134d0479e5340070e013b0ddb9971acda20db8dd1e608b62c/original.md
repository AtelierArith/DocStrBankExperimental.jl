```
initialparameters

Returns the initial parameters of a model, i.e., a layer or chain.
```

```
initialparameters(backend::NeuralNetworkBackend, ::Type{T}, model::Model; init::Initializer = default_initializer(), rng::AbstractRNG = Random.default_rng())
initialparameters(::Type{T}, model::Model; init::Initializer = default_initializer(), rng::AbstractRNG = Random.default_rng())
```

The `init!` function must have the following signature:

```
init!(rng::AbstractRNG, x::AbstractArray)
```

The `default_initializer()` returns `randn!`.
