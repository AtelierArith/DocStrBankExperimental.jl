```
mutable struct TTN{T}
    sites::Vector{Index{T}}
    graph::Graph{Int2}
    tensors::Dict{Int2, ITensor}
    orthocenter::Int2
end
```

ツリーテンソルネットワーク (TTN) オブジェクト。

各テンソルは整数のタプル (`::Int2`)、`(ll, nn)` によってインデックス付けされており、ここで (通常) `ll` はレイヤーインデックスを、`nn` は各レイヤーでのテンソルインデックスを示します。

  * `sites::Vector{Index}`: 物理サイト `Index`。
  * `graph::Graph{Int2}`: `Graph{Int2}` によって定義されたネットワークの基盤構造。
  * `tensors::Dict{Int2, ITensor}`: TTN 内のテンソル。
  * `orthocenter::Int2`: TTN の直交中心。
