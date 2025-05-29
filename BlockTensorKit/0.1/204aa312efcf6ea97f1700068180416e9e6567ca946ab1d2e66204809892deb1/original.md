```
struct SparseBlockTensorMap{TT<:AbstractTensorMap{E,S,N₁,N₂}} <: AbstractBlockTensorMap{E,S,N₁,N₂}
```

Sparse `SparseBlockTensorMap` type that stores tensors of type `TT` in a sparse dictionary.
