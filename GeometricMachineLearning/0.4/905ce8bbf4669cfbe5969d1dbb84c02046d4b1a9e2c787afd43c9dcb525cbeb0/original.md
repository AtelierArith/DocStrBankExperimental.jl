```
decoder(nn)
```

Make a neural network of type [`Decoder`](@ref) out of an arbitrary neural network.

# Implementation

Internally this allocates a new nerual network of type [`UnknownDecoder`](@ref) and takes the parameters and the backend from `nn`.
