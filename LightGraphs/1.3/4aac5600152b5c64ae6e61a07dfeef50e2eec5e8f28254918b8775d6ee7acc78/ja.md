```
k_core(g[, k]; corenum=core_number(g))
```

グラフ `g` の k-core に含まれる頂点のベクトルを返します。`k` が指定されていない場合、最大の次数を持つコアを返します。

k-core は、次数が `k` 以上の頂点を含む最大の部分グラフです。

### 実装ノート

自己ループを持つグラフには未実装です。

### 参考文献

  * An O(m) Algorithm for Cores Decomposition of Networks,   Vladimir Batagelj and Matjaz Zaversnik, 2003.   http://arxiv.org/abs/cs.DS/0310049

# 例

```jldoctest
julia> using LightGraphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_core(g, 1)
5-element Array{Int64,1}:
 1
 2
 3
 4
 5

julia> k_core(g, 2)
4-element Array{Int64,1}:
 2
 3
 4
 5    
```
