```
struct SparseBlockTensorMap{TT<:AbstractTensorMap{E,S,N₁,N₂}} <: AbstractBlockTensorMap{E,S,N₁,N₂}
```

スパース `SparseBlockTensorMap` 型は、タイプ `TT` のテンソルをスパース辞書に格納します。
