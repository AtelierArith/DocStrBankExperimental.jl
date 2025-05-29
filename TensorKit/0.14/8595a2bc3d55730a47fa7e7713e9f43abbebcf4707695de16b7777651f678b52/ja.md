```
space(t::AbstractTensorMap{T,S,N₁,N₂}) -> HomSpace{S,N₁,N₂}
space(t::AbstractTensorMap{T,S,N₁,N₂}, i::Int) -> S
```

テンソルのインデックス情報、すなわちその定義域と値域の `HomSpace`。`i` が指定されている場合、`i` 番目のインデックス空間を返します。
