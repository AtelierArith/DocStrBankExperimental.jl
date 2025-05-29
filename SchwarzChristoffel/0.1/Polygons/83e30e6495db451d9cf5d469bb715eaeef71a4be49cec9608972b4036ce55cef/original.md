```
Polygon(x::Vector{Float64}, y::Vector{Float64})
```

A polygon defined by its vertices, which must be provided in counter-clockwise order.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0])
Polygon with 4 vertices at
             (-1.0,-1.0) (0.2,-1.0) (1.0,0.5) (-1.0,1.0)
             interior angles/π = [0.5, 0.656, 0.422, 0.422]
```
