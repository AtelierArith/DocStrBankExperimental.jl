```
SymbolicNeuralNetwork(; n_input = 1, n_output = 1,
    chain = multi_layer_feed_forward(n_input, n_output),
    rng = Xoshiro(0),
    init_params = Lux.initialparameters(rng, chain),
    nn_name =  :NN,
    nn_p_name = :p,
    eltype = Float64)
```

Create symbolic parameter for a neural network and one for its parameters. Example:

```
chain = multi_layer_feed_forward(2, 2)
NN, p = SymbolicNeuralNetwork(; chain, n_input=2, n_output=2, rng = StableRNG(42))
```

The NN and p are symbolic parameters that can be used later as part of a system. To change the name of the symbolic variables, use `nn_name` and `nn_p_name`. To get the predictions of the neural network, use

```
pred ~ NN(input, p)
```

where `pred` and `input` are a symbolic vector variable with the lengths `n_output` and `n_input`.

To use this outside of an equation, you can get the default values for the symbols and make a similar call

```
defaults(sys)[sys.NN](input, nn_p)
```

where `sys` is a system (e.g. `ODESystem`) that contains `NN`, `input` is a vector of `n_input` length and `nn_p` is a vector representing parameter values for the neural network.

To get the underlying Lux model you can use `get_network(defaults(sys)[sys.NN])` or
