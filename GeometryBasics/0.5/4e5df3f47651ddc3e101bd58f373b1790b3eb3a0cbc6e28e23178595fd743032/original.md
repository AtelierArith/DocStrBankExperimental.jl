```
Polygon(exterior::AbstractVector{<:Point})
Polygon(exterior::AbstractVector{<:Point}, interiors::Vector{<:AbstractVector{<:Point}})
```

Constructs a polygon from a set of exterior points. If interiors are given, each of them cuts away from the Polygon.
