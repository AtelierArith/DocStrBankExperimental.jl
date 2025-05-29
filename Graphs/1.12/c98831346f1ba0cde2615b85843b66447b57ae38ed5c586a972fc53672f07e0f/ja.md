```
k_crust(g[, k]; corenum=core_number(g))
```

`g`のk-crustにある頂点のベクトルを返します。`k`が指定されていない場合、最大次数のコアのクラスターを返します。

k-crustは、[`k-core`](@ref k_core)が削除されたグラフ`g`です。

### 実装ノート

このk-crustの定義は、参考文献の定義とは異なります。参考文献のk-crustは、このアルゴリズムの`k+1`クラスターに相当します。

自己ループを持つグラフには未実装です。

### 参考文献

  * A model of Internet topology using k-shell decomposition  Shai Carmi, Shlomo Havlin, Scott Kirkpatrick, Yuval Shavitt,  and Eran Shir, PNAS  July 3, 2007   vol. 104  no. 27  11150-11154  http://www.pnas.org/content/104/27/11150.full

# 例

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_crust(g, 0)
1-element Vector{Int64}:
 6

julia> k_crust(g, 1)
2-element Vector{Int64}:
 1
 6

julia> k_crust(g, 2)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
