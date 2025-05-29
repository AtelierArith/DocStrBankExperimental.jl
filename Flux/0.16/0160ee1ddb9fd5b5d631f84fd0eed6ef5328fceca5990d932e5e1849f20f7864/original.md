```
GRUCell(in => out; init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[Gated Recurrent Unit](https://arxiv.org/abs/1406.1078v1) layer.  Behaves like an RNN but generally exhibits a longer memory span over sequences.  This implements the variant proposed in v1 of the referenced paper.

In the forward pass, computes

$$
r = \sigma(W_{xi} x + W_{hi} h + b_i)
z = \sigma(W_{xz} x + W_{hz} h + b_z)
h̃ = \tanh(W_{xh} x + r \odot W_{hh} h + b_h)
h' = (1 - z) \odot h̃ + z \odot h
$$

See also [`GRU`](@ref) for a layer that processes entire sequences.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
grucell(x, h)
grucell(x)
```

The arguments of the forward pass are:

  * `x`: The input to the GRU. It should be a vector of size `in` or a matrix of size `in x batch_size`.
  * `h`: The hidden state of the GRU. It should be a vector of size `out` or a matrix of size `out x batch_size`. If not provided, it is assumed to be a vector of zeros, initialized by [`initialstates`](@ref).

Returns the tuple `(output, state)`, where `output = h'` and `state = h'`. The new hidden state `h'` is an array of size `out` or `out x batch_size`.

# Examples

```jldoctest
julia> g = GRUCell(3 => 5)
GRUCell(3 => 5)     # 135 parameters

julia> h = zeros(Float32, 5); # hidden state

julia> x = rand(Float32, 3, 4);  # in x batch_size

julia> y, h = g(x, h);
```
