```
GRUv3Cell(in => out; init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[Gated Recurrent Unit](https://arxiv.org/abs/1406.1078v3) layer.  Behaves like an RNN but generally exhibits a longer memory span over sequences.  This implements the variant proposed in v3 of the referenced paper.

The forward pass computes

$$
r = \sigma(W_{xi} x + W_{hi} h + b_i)
z = \sigma(W_{xz} x + W_{hz} h + b_z)
h̃ = \tanh(W_{xh} x + W_{hh̃} (r \odot W_{hh} h) + b_h)
h' = (1 - z) \odot h̃ + z \odot h
$$

and returns `h'`. This is a single time step of the GRU.

See [`GRUv3`](@ref) for a layer that processes entire sequences. See [`GRU`](@ref) and [`GRUCell`](@ref) for variants of this layer.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
gruv3cell(x, [h])
```

The arguments of the forward pass are:

  * `x`: The input to the GRU. It should be a vector of size `in` or a matrix of size `in x batch_size`.
  * `h`: The hidden state of the GRU. It should be a vector of size `out` or a matrix of size `out x batch_size`. If not provided, it is assumed to be a vector of zeros, initialized by [`initialstates`](@ref).

Returns the tuple `(output, state)`, where `output = h'` and `state = h'`.   The new hidden state `h'` is an array of size `out` or `out x batch_size`.
