```
vertex(p::Polygon) -> Vector{ComplexF64}
```

Returns the vector of vertices of the polygon `p`, in complex form.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> vertex(p)
4-element Array{Complex{Float64},1}:
 -1.0-1.0im
  0.2-1.0im
  1.0+0.5im
 -1.0+1.0im
```
