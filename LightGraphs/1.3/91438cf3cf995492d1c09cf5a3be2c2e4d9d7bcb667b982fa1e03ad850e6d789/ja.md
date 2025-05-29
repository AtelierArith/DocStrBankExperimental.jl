```
connected_components(g)
```

無向グラフ `g` の [連結成分](https://en.wikipedia.org/wiki/Connectivity_(graph_theory)) を成分のベクトルとして返します。各要素はその成分に属する頂点のベクトルです。

有向グラフについては、[`strongly_connected_components`](@ref) および [`weakly_connected_components`](@ref) を参照してください。

# 例

```jldoctest
julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> connected_components(g)
1-element Array{Array{Int64,1},1}:
 [1, 2, 3]

julia> g = SimpleGraph([0 1 0 0 0; 1 0 1 0 0; 0 1 0 0 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> connected_components(g)
2-element Array{Array{Int64,1},1}:
 [1, 2, 3]
 [4, 5]
```
