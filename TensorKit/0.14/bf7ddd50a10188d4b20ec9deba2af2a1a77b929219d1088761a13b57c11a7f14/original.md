```
struct TensorMap{T, S<:IndexSpace, N₁, N₂, A<:DenseVector{T}} <: AbstractTensorMap{T, S, N₁, N₂}
```

Specific subtype of [`AbstractTensorMap`](@ref) for representing tensor maps (morphisms in a tensor category), where the data is stored in a dense vector.
