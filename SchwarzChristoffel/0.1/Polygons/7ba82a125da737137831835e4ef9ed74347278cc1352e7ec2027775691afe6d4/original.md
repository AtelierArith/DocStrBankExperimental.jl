```
interiorangle(p::Polygon) -> Vector{Float64}
```

Returns the vector of interior angles (divided by $\pi$) of the polygon `p`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> interiorangle(p)
4-element Array{Float64,1}:
 0.5
 0.655958
 0.422021
 0.422021
```
