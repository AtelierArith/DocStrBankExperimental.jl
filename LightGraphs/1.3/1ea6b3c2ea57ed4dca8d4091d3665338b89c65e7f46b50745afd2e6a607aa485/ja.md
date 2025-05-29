```
k_shell(g[, k]; corenum=core_number(g))
```

グラフ `g` の k-shell にある頂点のベクトルを返します。`k` が指定されていない場合は、最大次数のコアのシェルを返します。

k-shell は、`k`-コアにある頂点の部分グラフですが、(`k+1`)-コアには含まれません。これは `k_corona` に似ていますが、その場合は k-core の隣接点のみが考慮されます。

### 実装ノート

平行エッジや自己ループを持つグラフには未実装です。

### 参考文献

  * A model of Internet topology using k-shell decomposition  Shai Carmi, Shlomo Havlin, Scott Kirkpatrick, Yuval Shavitt,  and Eran Shir, PNAS  July 3, 2007   vol. 104  no. 27  11150-11154  http://www.pnas.org/content/104/27/11150.full

# 例

```jldoctest
julia> using LightGraphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_shell(g, 0)
1-element Array{Int64,1}:
 6

julia> k_shell(g, 1)
1-element Array{Int64,1}:
 1

julia> k_shell(g, 2)
4-element Array{Int64,1}:
 2
 3
 4
 5
```
