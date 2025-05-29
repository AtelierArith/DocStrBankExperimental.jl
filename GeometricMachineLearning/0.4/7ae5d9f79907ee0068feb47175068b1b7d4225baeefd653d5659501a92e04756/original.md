```
SymplecticAttentionQ
```

A constant that is derived from [`SymplecticAttention`](@ref). This only changes the $q$-part of the input.

# Constructor

```julia
SymplecticAttentionQ(M; symmetric::Bool, activation)
```

The default for the keywords are true and GeometricMachineLearning.MatrixSoftmax().

You may want to alter the activation function (either [`MatrixSoftmax`](@ref) or [`VectorSoftmax`](@ref)), but its almost always better to set the keyword `symmetric` to `true`.
