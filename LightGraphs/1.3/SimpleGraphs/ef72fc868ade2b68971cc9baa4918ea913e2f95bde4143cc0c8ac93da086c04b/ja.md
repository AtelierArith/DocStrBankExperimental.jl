```
SimpleGraph(g::SimpleDiGraph)
```

有向 `SimpleDiGraph` から無向 `SimpleGraph` を構築します。`g` のすべての有向エッジは無向エッジとして追加されます。要素の型は `g` と同じです。

## 例

```jldoctest
julia> g = path_digraph(Int8(5))
julia> SimpleGraph(g)
{5, 4} 無向単純 Int8 グラフ
```
