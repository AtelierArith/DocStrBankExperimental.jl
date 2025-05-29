```
struct BlockTensorMap{TT<:AbstractTensorMap{E,S,N₁,N₂}} <: AbstractTensorMap{E,S,N₁,N₂}
```

Dense `BlockTensorMap` type that stores tensors of type `TT` in a dense array.
