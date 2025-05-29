```
Polygon(w::Vector{ComplexF64})
```

Sets up a polygon with the coordinates of the vertices specified with complex vector `w`. As usual, these must be supplied in counter-clockwise order.

# Example

```jldoctest
julia> p = Polygon([-1.0-1.0im,0.2-1.0im,1.0+0.5im,-1.0+1.0im])
Polygon with 4 vertices at
             (-1.0,-1.0) (0.2,-1.0) (1.0,0.5) (-1.0,1.0)
             interior angles/π = [0.5, 0.656, 0.422, 0.422]
```
