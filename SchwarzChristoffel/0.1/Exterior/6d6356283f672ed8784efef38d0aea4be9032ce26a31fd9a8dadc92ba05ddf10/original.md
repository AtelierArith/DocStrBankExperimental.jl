```
moments(m::ExteriorMap) -> Vector{ComplexF64}
```

Return the moments of the prevertices for exterior polygon mapping `m`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> mom = moments(m);
```
