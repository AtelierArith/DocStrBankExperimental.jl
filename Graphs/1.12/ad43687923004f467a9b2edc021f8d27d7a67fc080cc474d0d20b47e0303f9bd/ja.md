```
strongly_connected_components_kosaraju(g)
```

有向グラフ `g` の強連結成分をコサラジュのアルゴリズムを使用して計算します。(https://en.wikipedia.org/wiki/Kosaraju%27s_algorithm)。

全ての連結成分を含む配列の配列を返します。

### パフォーマンス

時間計算量 : O(|E|+|V|) 空間計算量 : O(|V|) {グラフを保存するために必要なメモリを除く}

|V| = 頂点の数 |E| = 辺の数

### 例

```jldoctest
julia> using Graphs

julia> g=SimpleDiGraph(3)
{3, 0} directed simple Int64 graph

julia> g = SimpleDiGraph([0 1 0 ; 0 0 1; 0 0 0])
{3, 2} directed simple Int64 graph

julia> strongly_connected_components_kosaraju(g)
3-element Vector{Vector{Int64}}:
 [1]
 [2]
 [3]


julia> g=SimpleDiGraph(11)
{11, 0} directed simple Int64 graph

julia> edge_list=[(1,2),(2,3),(3,4),(4,1),(3,5),(5,6),(6,7),(7,5),(5,8),(8,9),(9,8),(10,11),(11,10)]
13-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (2, 3)
 (3, 4)
 (4, 1)
 (3, 5)
 (5, 6)
 (6, 7)
 (7, 5)
 (5, 8)
 (8, 9)
 (9, 8)
 (10, 11)
 (11, 10)

julia> g = SimpleDiGraph(Edge.(edge_list))
{11, 13} directed simple Int64 graph

julia> strongly_connected_components_kosaraju(g)
4-element Vector{Vector{Int64}}:
 [11, 10]
 [2, 3, 4, 1]
 [6, 7, 5]
 [9, 8]

```
