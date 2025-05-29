```
core_number(g)
```

グラフ `g` の各頂点のコア数を返します。

kコアは、次数が `k` 以上の頂点を含む最大の部分グラフです。頂点のコア数は、その頂点を含むkコアの最大値 `k` です。

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

julia> core_number(g)
6-element Array{Int64,1}:
 1
 2
 2
 2
 2
 0
```
