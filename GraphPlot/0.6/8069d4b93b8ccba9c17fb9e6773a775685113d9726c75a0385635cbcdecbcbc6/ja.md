この関数は[IainNZ](https://github.com/IainNZ)の[GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl)からコピーしたものです。

同心円にノードを配置します。

**パラメータ**

*g* グラフ

*nlist* 各シェルのノードのベクトルのベクトル。

**例**

```
julia> g = smallgraph(:karate)
julia> nlist = Vector{Vector{Int}}()
julia> push!(nlist, collect(1:5))
julia> push!(nlist, collect(6:nv(g)))
julia> locs_x, locs_y = shell_layout(g, nlist)
```
