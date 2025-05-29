```
Recurrence(cell)
```

Create a recurrent layer that processes entire sequences out of a recurrent `cell`, such as an [`RNNCell`](@ref), [`LSTMCell`](@ref), or [`GRUCell`](@ref), similarly to how [`RNN`](@ref), [`LSTM`](@ref), and [`GRU`](@ref) process sequences.

The `cell` should be a callable object that takes an input `x` and a hidden state `state` and returns a new hidden state `state'`. The `cell` should also implement the `initialstates` method that returns the initial hidden state. The output of the `cell` is considered to be:

1. The first element of the `state` tuple if `state` is a tuple (e.g. `(h, c)` for LSTM).
2. The `state` itself if `state` is not a tuple, e.g. an array `h` for RNN and GRU.

# Forward

```
rnn(x, [state])
```

The input `x` should be an array of size `in x len` or `in x len x batch_size`,  where `in` is the input dimension of the cell, `len` is the sequence length, and `batch_size` is the batch size. The `state` should be a valid state for the recurrent cell. If not provided, it obtained by calling `Flux.initialstates(cell)`.

The output is an array of size `out x len x batch_size`, where `out` is the output dimension of the cell.

The operation performed is semantically equivalent to the following code:

```julia
out_from_state(state) = state
out_from_state(state::Tuple) = state[1]

state = Flux.initialstates(cell)
out = []
for x_t in eachslice(x, dims = 2)
  state = cell(x_t, state)
  out = [out..., out_from_state(state)]
end
stack(out, dims = 2)
```

# Examples

```jldoctest
julia> rnn = Recurrence(RNNCell(2 => 3))
Recurrence(
  RNNCell(2 => 3, tanh),                # 18 parameters
)                   # Total: 3 arrays, 18 parameters, 232 bytes.

julia> x = rand(Float32, 2, 3, 4); # in x len x batch_size

julia> y = rnn(x); # out x len x batch_size
```
