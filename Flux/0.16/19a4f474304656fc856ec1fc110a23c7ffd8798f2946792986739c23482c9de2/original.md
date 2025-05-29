```
initialstates(rnn) -> AbstractVector
```

Return the initial hidden state for the given recurrent cell or recurrent layer.

# Example

```julia
using Flux

# Create an RNNCell from input dimension 10 to output dimension 20
rnn = RNNCell(10 => 20)

# Get the initial hidden state
state = initialstates(rnn)

# Get some input data
x = rand(Float32, 10)

# Run forward
out, state = rnn(x, state)
```
