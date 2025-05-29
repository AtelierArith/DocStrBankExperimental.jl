```
subspace(v)
```

頂点 `v` に接続された部分空間を返します。

```jldoctest; setup = :(using QSWalk)
julia> v = Vertex([1,2,3])
Vertex([1, 2, 3])

julia> subspace(v)
3-element Array{Int64,1}:
 1
 2
 3
```
