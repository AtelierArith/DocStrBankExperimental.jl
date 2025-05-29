```
LSTM(in => out; return_state = false, init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[Long Short Term Memory](https://www.researchgate.net/publication/13853244_Long_Short-term_Memory) recurrent layer. Behaves like an RNN but generally exhibits a longer memory span over sequences.

See [this article](https://colah.github.io/posts/2015-08-Understanding-LSTMs/) for a good overview of the internals.

In the forward pass, computes

$$
i_t = \sigma(W_{xi} x_t + W_{hi} h_{t-1} + b_i)
f_t = \sigma(W_{xf} x_t + W_{hf} h_{t-1} + b_f)
c_t = f_t \odot c_{t-1} + i_t \odot \tanh(W_{xc} x_t + W_{hc} h_{t-1} + b_c)
o_t = \sigma(W_{xo} x_t + W_{ho} h_{t-1} + b_o)
h_t = o_t \odot \tanh(c_t)
$$

for all `len` steps `t` in the input sequence. See [`LSTMCell`](@ref) for a layer that processes a single time step.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `return_state`: Option to return the last state together with the output. Default is `false`.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
lstm(x, (h, c))
lstm(x)
```

The arguments of the forward pass are:

  * `x`: The input to the LSTM. It should be a matrix of size `in x len` or an array of size `in x len x batch_size`.
  * `(h, c)`: A tuple containing the hidden and cell states of the LSTM.    They should be vectors of size `out` or matrices of size `out x batch_size`.   If not provided, they are assumed to be vectors of zeros, initialized by [`initialstates`](@ref).

Returns all new hidden states `h_t` as an array of size `out x len` or `out x len x batch_size`. When `return_state = true` it returns a tuple of the hidden stats `h_t` and the last state of the iteration.

# Examples

```julia
struct Model
  lstm::LSTM
  h0::AbstractVector # trainable initial hidden state
  c0::AbstractVector
end

Flux.@layer Model

(m::Model)(x) = m.lstm(x, (m.h0, m.c0))

d_in, d_out, len, batch_size = 2, 3, 4, 5
x = rand(Float32, (d_in, len, batch_size))
model = Model(LSTM(d_in => d_out), zeros(Float32, d_out), zeros(Float32, d_out))
h = model(x)
size(h)  # out x len x batch_size
```
