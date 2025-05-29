```
VF2Matcher{T,U,G<:SimpleGraph{T},H<:SimpleGraph{U}}
```

`G`と`H`の間のすべての同型写像を生成する遅延イテレータです。

`matchtype`は次のいずれかである必要があります。

  * `:isomorphic`: GはHと同型です
  * `:subgraph_isomorphic`: Gのノード誘導部分グラフはHと同型です
  * `:monomorphic`: Gの部分グラフはHに単射です

# オプション

  * `vmatch::Function`: セマンティックノード属性マッチングのための関数（デフォルト: (a, b) -> true）
  * `ematch::Function`: セマンティックエッジ属性マッチングのための関数（デフォルト: (a, b) -> true）
  * `mandatory::Dict{Int,Int}`: 必須ノードマッピング（matchtype=:edgeinducedの場合、エッジマッピング）
  * `forbidden::Dict{Int,Int}`: 禁止ノードマッピング（matchtype=:edgeinducedの場合、エッジマッピング）
  * `timeout::Union{Int,Nothing}`: 指定された場合、時間が経過したときにvf2計算を中止し、空のイテレータを返します（デフォルト: 10秒）
