```
weakly_connected_components(g)
```

グラフ `g` の弱連結成分を返します。これは `g` の無向同等物の連結成分に相当します。無向グラフの場合、これは `g` の [`connected_components`](@ref) に相当します。

# 例

```jldoctest
julia> g = DiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> weakly_connected_components(g)
1-element Array{Array{Int64,1},1}:
 [1, 2, 3]
```
