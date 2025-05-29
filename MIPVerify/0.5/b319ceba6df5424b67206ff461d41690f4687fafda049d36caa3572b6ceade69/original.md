```julia
abstract type NeuralNet
```

Supertype for all types storing the parameters of a neural net. Inherit from this to specify your own custom architecture. Each implementation is expected to:

1. Implement a callable specifying the output when any input of type `JuMPReal` is provided
2. Have a `UUID` field for the name of the neural network.
