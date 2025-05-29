```
Polygon(x::Vector{Float64}, y::Vector{Float64})
```

頂点によって定義される多角形で、頂点は反時計回りの順序で提供する必要があります。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0])
Polygon with 4 vertices at
             (-1.0,-1.0) (0.2,-1.0) (1.0,0.5) (-1.0,1.0)
             interior angles/π = [0.5, 0.656, 0.422, 0.422]
```
