```
struct BlockTensorMap{TT<:AbstractTensorMap{E,S,N₁,N₂}} <: AbstractTensorMap{E,S,N₁,N₂}
```

密な配列にタイプ `TT` のテンソルを格納する密な `BlockTensorMap` タイプ。
