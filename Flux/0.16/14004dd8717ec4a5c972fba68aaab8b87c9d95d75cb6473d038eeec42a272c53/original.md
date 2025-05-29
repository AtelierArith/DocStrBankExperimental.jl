```
LSTMCell(in => out; init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

The [Long Short Term Memory](https://www.researchgate.net/publication/13853244_Long_Short-term_Memory) cell. Behaves like an RNN but generally exhibits a longer memory span over sequences.

In the forward pass, computes

$$
i_t = \sigma(W_{xi} x_t + W_{hi} h_{t-1} + b_i)
f_t = \sigma(W_{xf} x_t + W_{hf} h_{t-1} + b_f)
c_t = f_t \odot c_{t-1} + i_t \odot \tanh(W_{xc} x_t + W_{hc} h_{t-1} + b_c)
o_t = \sigma(W_{xo} x_t + W_{ho} h_{t-1} + b_o)
h_t = o_t \odot \tanh(c_t)
$$

See also [`LSTM`](@ref) for a layer that processes entire sequences.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
lstmcell(x, (h, c))
lstmcell(x)
```

The arguments of the forward pass are:

  * `x`: The input to the LSTM. It should be a matrix of size `in` or an array of size `in x batch_size`.
  * `(h, c)`: A tuple containing the hidden and cell states of the LSTM.  They should be vectors of size `out` or matrices of size `out x batch_size`. If not provided, they are assumed to be vectors of zeros, initialized by [`initialstates`](@ref).

Returns a tuple `(output, state)`, where `output = h'` is the new hidden state and `state = (h', c')` is the new hidden and cell states. These are tensors of size `out` or `out x batch_size`. 

# Examples

```jldoctest
julia> l = LSTMCell(3 => 5)
LSTMCell(3 => 5)    # 180 parameters

julia> h = zeros(Float32, 5); # hidden state

julia> c = zeros(Float32, 5); # cell state

julia> x = rand(Float32, 3, 4);  # in x batch_size

julia> y, (h′, c′) = l(x, (h, c));

julia> size(y)  # out x batch_size
(5, 4)
```
