```
connected_components(g)
```

無向グラフ `g` の[連結成分](https://en.wikipedia.org/wiki/Connectivity_(graph_theory))を、各要素が成分に属する頂点のベクトルである成分のベクトルとして返します。

有向グラフについては、[`strongly_connected_components`](@ref)および[`weakly_connected_components`](@ref)を参照してください。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> connected_components(g)
1-element Vector{Vector{Int64}}:
 [1, 2, 3]

julia> g = SimpleGraph([0 1 0 0 0; 1 0 1 0 0; 0 1 0 0 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> connected_components(g)
2-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [4, 5]
```
