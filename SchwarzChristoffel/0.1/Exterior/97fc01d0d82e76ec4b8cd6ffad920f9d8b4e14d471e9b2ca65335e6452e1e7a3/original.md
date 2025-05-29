```
area(m::ConformalMap) -> Float64
```

Returns the area of the shape described by the mapping `m`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> area(m)
2.9
```

```jldoctest
julia> c = ComplexF64[1];

julia> m = PowerMap(c);

julia> area(m)
3.141592653589793
```
