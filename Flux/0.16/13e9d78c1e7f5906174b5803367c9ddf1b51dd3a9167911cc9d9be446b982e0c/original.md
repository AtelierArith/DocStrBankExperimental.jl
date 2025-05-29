```
RNN(in => out, σ = tanh; return_state = false,
  init_kernel = glorot_uniform, init_recurrent_kernel = glorot_uniform, bias = true)
```

The most basic recurrent layer. Essentially acts as a `Dense` layer, but with the output fed back into the input each time step.  

In the forward pass computes

$$
h_t = \sigma(W_i x_t + W_h h_{t-1} + b)
$$

for all `len` steps `t` in the in input sequence. 

See [`RNNCell`](@ref) for a layer that processes a single time step.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `σ`: The non-linearity to apply to the output. Default is `tanh`.
  * `return_state`: Option to return the last state together with the output. Default is `false`.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
rnn(x, [h])
```

The arguments of the forward pass are:

  * `x`: The input to the RNN. It should be a matrix size `in x len` or an array of size `in x len x batch_size`.
  * `h`: The initial hidden state of the RNN.       If given, it is a vector of size `out` or a matrix of size `out x batch_size`.      If not provided, it is assumed to be a vector of zeros, initialized by [`initialstates`](@ref).

Returns all new hidden states `h_t` as an array of size `out x len x batch_size`. When `return_state = true` it returns a tuple of the hidden stats `h_t` and the last state of the iteration.

# Examples

```jldoctest
julia> d_in, d_out, len, batch_size = 4, 6, 3, 5;

julia> x = rand(Float32, (d_in, len, batch_size));

julia> h = zeros(Float32, (d_out, batch_size));

julia> rnn = RNN(d_in => d_out)
RNN(4 => 6, tanh)   # 66 parameters

julia> y = rnn(x, h);   # [y] = [d_out, len, batch_size]
```

Sometimes, the initial hidden state is a learnable parameter.  In this case, the `RNN` should be wrapped in a custom struct.

```julia
struct Model
  rnn::RNN
  h0::AbstractVector
end

Flux.@layer Model

(m::Model)(x) = m.rnn(x, m.h0)

model = Model(RNN(32 => 64), zeros(Float32, 64))
```
