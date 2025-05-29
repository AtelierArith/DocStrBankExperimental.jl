```
isinpoly(z::Complex128,p::Polygon,tol::Float64) -> Bool
```

Returns `true` if `z` is inside or within distance `tol` of polygon `p`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> isinpoly(-1.01+0.0im,p)
false

julia> isinpoly(-1.01+0.0im,p,1e-2)
true
```
