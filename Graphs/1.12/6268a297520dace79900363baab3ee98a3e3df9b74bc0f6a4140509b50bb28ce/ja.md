```
attracting_components(g)
```

有向グラフ `g` の魅力的成分のリストを表す整数のベクトルのベクトルを返します。

魅力的成分は、出て行くエッジを持たない強連結成分のサブセットです。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0])
{5, 6} directed simple Int64 graph

julia> strongly_connected_components(g)
2-element Vector{Vector{Int64}}:
 [4, 5]
 [1, 2, 3]

julia> attracting_components(g)
1-element Vector{Vector{Int64}}:
 [4, 5]
```
