```
SymmetricAdapter{T} <: Adapter{T, T}
```

Abstract adapter type. `encode` both for serializing and deserializing.

## Methods

  * [`subcon(adapter::SymmetricAdapter{T})`](@ref subcon)
  * [`encode(adapter::SymmetricAdapter{T}, obj::T; contextkw...)`](@ref encode)
