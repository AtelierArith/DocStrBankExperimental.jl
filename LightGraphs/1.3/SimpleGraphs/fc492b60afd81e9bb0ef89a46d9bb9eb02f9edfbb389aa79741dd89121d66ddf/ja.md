```
SimpleGraph(edge_list::Vector)
```

ベクトルのエッジから`SimpleGraph`を構築します。要素の型は`edge_list`内のエッジから取得されます。頂点の数は`edge_list`内のエッジで使用される最大の値です。

### 実装ノート

このコンストラクタは、`edge_list`が辞書順でソートされており、重複が含まれていない場合に最も高速に動作します。

### 参照

[`SimpleGraphFromIterator`](@ref)

## 例

```jldoctest

julia> el = Edge.([ (1, 2), (1, 5) ])
julia> SimpleGraph(el)
{5, 2} undirected simple Int64 graph
```
