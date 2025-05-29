```
Polygon(w::Vector{ComplexF64})
```

複素ベクトル `w` で指定された頂点の座標を持つ多角形を設定します。通常通り、これらは反時計回りの順序で提供する必要があります。

# 例

```jldoctest
julia> p = Polygon([-1.0-1.0im,0.2-1.0im,1.0+0.5im,-1.0+1.0im])
Polygon with 4 vertices at
             (-1.0,-1.0) (0.2,-1.0) (1.0,0.5) (-1.0,1.0)
             interior angles/π = [0.5, 0.656, 0.422, 0.422]
```
