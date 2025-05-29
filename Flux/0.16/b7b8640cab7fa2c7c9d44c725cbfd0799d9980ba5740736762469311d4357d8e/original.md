```
RNNCell(in => out, σ = tanh; init_kernel = glorot_uniform, 
  init_recurrent_kernel = glorot_uniform, bias = true)
```

The most basic recurrent layer. Essentially acts as a `Dense` layer, but with the output fed back into the input each time step.

In the forward pass, implements the function

$$
h^\prime = \sigma(W_i x + W_h h + b)
$$

See [`RNN`](@ref) for a layer that processes entire sequences.

# Arguments

  * `in => out`: The input and output dimensions of the layer.
  * `σ`: The non-linearity to apply to the output. Default is `tanh`.
  * `init_kernel`: The initialization function to use for the input to hidden connection weights. Default is `glorot_uniform`.
  * `init_recurrent_kernel`: The initialization function to use for the hidden to hidden connection weights. Default is `glorot_uniform`.
  * `bias`: Whether to include a bias term initialized to zero. Default is `true`.

# Forward

```
rnncell(x, [h])
```

The arguments of the forward pass are:

  * `x`: The input to the RNN. It should be a vector of size `in` or a matrix of size `in x batch_size`.
  * `h`: The hidden state of the RNN. It should be a vector of size `out` or a matrix of size `out x batch_size`.      If not provided, it is assumed to be a vector of zeros, initialized by [`initialstates`](@ref).

Returns a tuple `(output, state)`, where both elements are given by the updated state `h'`,  a tensor of size `out` or `out x batch_size`.

# Examples

```julia
r = RNNCell(3 => 5)

# A sequence of length 10 and batch size 4
x = [rand(Float32, 3, 4) for _ in 1:10]

# Initialize the hidden state
h = zeros(Float32, 5)

# We collect the hidden states in an array `history`
# in case the loss depends on the entire sequence.
ŷ = []

for x_t in x
  yt, h = r(x_t, h)
  ŷ = [ŷ..., yt] # Cannot use `push!(ŷ, h)` here since mutation 
                 # is not automatic differentiation friendly yet.
                 # Can use `y = vcat(y, [h])` as an alternative.
end

h   # The final hidden state
ŷ   # The hidden states at each time step
```
