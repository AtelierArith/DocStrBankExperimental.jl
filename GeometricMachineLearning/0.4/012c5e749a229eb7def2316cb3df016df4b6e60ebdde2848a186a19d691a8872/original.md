```
encoder(nn)
```

Make a neural network of type [`Encoder`](@ref) out of an arbitrary neural network.

# Implementation

Internally this allocates a new nerual network of type [`UnknownEncoder`](@ref) and takes the parameters and the backend from `nn`.
