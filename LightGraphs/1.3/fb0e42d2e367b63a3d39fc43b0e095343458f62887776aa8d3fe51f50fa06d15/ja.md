```
core_periphery_deg(g)
```

グラフ `g` の次数ベースのコア-ペリフェリーを計算します。`g` の各ノードに対する頂点の割り当て（コアには `1`、ペリフェリーには `2`）を返します。

参考文献:     [Lip](http://arxiv.org/abs/1102.5511))

# 例

```jldoctest
julia> using LightGraphs

julia> core_periphery_deg(star_graph(5))
5-element Array{Int64,1}:
 1
 2
 2
 2
 2

julia> core_periphery_deg(path_graph(3))
3-element Array{Int64,1}:
 2
 1
 2
```
