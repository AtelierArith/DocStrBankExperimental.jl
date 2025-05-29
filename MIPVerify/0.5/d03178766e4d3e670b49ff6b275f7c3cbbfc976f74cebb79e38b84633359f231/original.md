```julia
abstract type Layer
```

Supertype for all types storing the parameters of each layer. Inherit from this to specify your own custom type of layer. Each implementation is expected to:

1. Implement a callable specifying the output when any input of type `JuMPReal` is provided.
