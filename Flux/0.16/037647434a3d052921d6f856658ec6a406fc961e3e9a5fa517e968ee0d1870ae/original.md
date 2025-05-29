```
GRU(in => out; return_state = false, init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[Gated Recurrent Unit](https://arxiv.org/abs/1406.1078v1) layer. Behaves like an RNN but generally exhibits a longer memory span over sequences. This implements the variant proposed in v1 of the referenced paper.

The forward pass computes

$$
r_t = \sigma(W_{xi} x_t + W_{hi} h_{t-1} + b_i)
z_t = \sigma(W_{xz} x_t + W_{hz} h_{t-1} + b_z)
h̃_t = \tanh(W_{xh} x_t + r_t \odot W_{hh} h_{t-1} + b_h)
h_t = (1 - z_t) \odot h̃_t + z_t \odot h_{t-1}
$$

for all `len` steps `t` in the input sequence. See [`GRUCell`](@ref) for a layer that processes a single time step.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `return_state`: Option to return the last state together with the output. Default is `false`.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
gru(x, [h])
```

The arguments of the forward pass are:

  * `x`: The input to the GRU. It should be a matrix of size `in x len` or an array of size `in x len x batch_size`.
  * `h`: The initial hidden state of the GRU. It should be a vector of size `out` or a matrix of size `out x batch_size`.      If not provided, it is assumed to be a vector of zeros, initialized by [`initialstates`](@ref).

Returns all new hidden states `h_t` as an array of size `out x len x batch_size`. When `return_state = true` it returns a tuple of the hidden stats `h_t` and the last state of the iteration.

# Examples

```julia
d_in, d_out, len, batch_size = 2, 3, 4, 5
gru = GRU(d_in => d_out)
x = rand(Float32, (d_in, len, batch_size))
h0 = zeros(Float32, d_out)
h = gru(x, h0)  # out x len x batch_size
```
