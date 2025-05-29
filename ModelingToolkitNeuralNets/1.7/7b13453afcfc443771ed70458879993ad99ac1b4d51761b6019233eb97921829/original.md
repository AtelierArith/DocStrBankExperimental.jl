```
NeuralNetworkBlock(; n_input = 1, n_output = 1,
    chain = multi_layer_feed_forward(n_input, n_output),
    rng = Xoshiro(0),
    init_params = Lux.initialparameters(rng, chain),
    eltype = Float64,
    name)
```

Create an `ODESystem` with a neural network inside.
