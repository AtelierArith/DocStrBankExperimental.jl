```
circular_ladder_graph(n)
```

`2n` ノードと `3n` エッジからなる [円形はしごグラフ](https://en.wikipedia.org/wiki/Ladder_graph#Circular_ladder_graph) を作成します。これは [プリズムグラフ](https://en.wikipedia.org/wiki/Prism_graph) とも呼ばれます。

### 実装ノート

パーティションベクターの eltype を保持します。必要な頂点数が eltype を超えるとエラーになります。自己ループや多重エッジを避けるために、`n` は少なくとも 3 でなければなりません。

# 例

```jldoctest
julia> circular_ladder_graph(3)
{6, 9} 無向単純 Int64 グラフ

julia> circular_ladder_graph(Int8(4))
{8, 12} 無向単純 Int8 グラフ
```
