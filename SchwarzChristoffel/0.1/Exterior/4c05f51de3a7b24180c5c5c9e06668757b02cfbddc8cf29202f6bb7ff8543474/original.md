```
addedmass(m::ConformalMap) -> Array{Float64,2}
```

Returns the added mass matrix of the shape described by the conformal mapping `m`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> addedmass(m)
3×3 Array{Float64,2}:
  0.725129    0.0944902  -1.37387
  0.0944902   3.67634    -0.255119
 -1.37387    -0.255119    3.59231
```
