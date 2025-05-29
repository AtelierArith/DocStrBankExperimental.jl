```
Optimizer(method, nn_params)
```

Allocate the cache for a specific `method` and `nn_params` for an instance of `Optimizer`.

Internally this calls [`init_optimizer_cache`](@ref).

An equivalent constructor is

```julia
Optimizer(method, nn::NeuralNetwork)
```

# Arguments

The optional keyword argument is the retraction. By default this is [`cayley`](@ref).
