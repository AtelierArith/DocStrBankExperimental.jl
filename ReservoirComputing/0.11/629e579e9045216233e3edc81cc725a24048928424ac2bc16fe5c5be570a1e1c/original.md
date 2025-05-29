```
GRU(;activation_function=[NNlib.sigmoid, NNlib.sigmoid, tanh],
    inner_layer = fill(DenseLayer(), 2),
    reservoir = fill(RandSparseReservoir(), 2),
    bias = fill(DenseLayer(), 2),
    variant = FullyGated())
```

Returns a Gated Recurrent Unit (GRU) reservoir driver for Echo State Network (`ESN`). This driver is based on the GRU architecture [^Cho2014].

# Arguments

  * `activation_function`: An array of activation functions for the GRU layers. By default, it uses sigmoid activation functions for the update gate, reset gate, and tanh for the hidden state.
  * `inner_layer`: An array of inner layers used in the GRU architecture. By default, it uses two dense layers.
  * `reservoir`: An array of reservoir layers. By default, it uses two random sparse reservoirs.
  * `bias`: An array of bias layers for the GRU. By default, it uses two dense layers.
  * `variant`: The GRU variant to use. By default, it uses the "FullyGated" variant.

[^Cho2014]: Cho, Kyunghyun, et al. "*Learning phrase representations using RNN encoder-decoder for statistical machine translation.*" arXiv preprint arXiv:1406.1078 (2014).
