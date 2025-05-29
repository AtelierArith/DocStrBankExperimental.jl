```
Jmoment(m::ConformalMap) -> Float64
```

Returns the second area moment of the shape described by the mapping `m`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> Jmoment(m)
1.5768333333333333
```
