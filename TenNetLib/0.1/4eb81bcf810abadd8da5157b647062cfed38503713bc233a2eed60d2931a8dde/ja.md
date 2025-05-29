```
mutable struct Graph{T}
    nodes::Set{T}
    edges::Dict{T, Set{T}}
end
```

ノードが型 `T` の無向グラフ。

  * `nodes::Set{T}`: グラフのノードを保持します。
  * `edges::Dict{T, Set{T}}`: グラフのエッジを保持します。特定のノードを `key` として、接続されたすべてのノードを `Dict` の `value` として保持します。
