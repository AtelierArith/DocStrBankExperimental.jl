```
struct Polygon{T} <: AbstractPolygon{T}
    p::Vector{Point{T}}
    Polygon(x) = new(x)
    Polygon(x::AbstractPolygon) = convert(Polygon{T}, x)
end
```

Polygon defined by list of coordinates. The first point should not be repeated at the end (although this is true for the GDS format).
