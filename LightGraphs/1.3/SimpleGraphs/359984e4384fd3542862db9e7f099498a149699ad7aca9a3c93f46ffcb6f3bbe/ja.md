```
rem_vertices!(g, vs, keep_order=false) -> vmap
```

`g`から`vs`のすべての頂点を削除します。修正されたグラフの頂点を未修正のグラフの頂点にマッピングするベクトル`vmap`を返します。`keep_order`が`true`の場合、修正されたグラフの頂点は未修正のグラフと同じ順序で表示されます。これは遅くなる可能性があります。

### 実装ノート

この関数は公式のLightGraphs APIの一部ではなく、メジャーバージョン間で変更または削除される可能性があります。

# 例

```jldoctest
julia> using LightGraphs

julia> g = complete_graph{5}
{5, 10} 無向単純 Int64 グラフ

julia> vmap = rem_vertices!(g, [2, 4], keep_order=true);

julia> vmap
3-element Array{Int64,1}:
 1
 3
 5

julia> g
{3, 3} 無向単純 Int64 グラフ
```
