```
isinpoly(z::Complex128,p::Polygon) -> Bool
```

Returns `true` or `false` depending on whether `z` is inside or outside polygon `p`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> isinpoly(0.0+0.0im,p)
true

julia> isinpoly(1.0+2.0im,p)
false
```
