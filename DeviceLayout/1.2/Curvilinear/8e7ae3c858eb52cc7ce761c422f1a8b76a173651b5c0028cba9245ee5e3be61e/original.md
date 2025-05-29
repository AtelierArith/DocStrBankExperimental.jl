```
struct CurvilinearPolygon{T} <: GeometryEntity{T}
    p::Vector{Point{T}}
    curves::Vector{<:Paths.Segment}
    curve_start_idx::Vector{Int}
end
```

A curvilinear polygon defined by a list of coordinates and curves between them. Straight sections are implicit, whereas any curve is specified by the start index. A `Polygon` can be represented using a `CurvilinearPolygon` with an empty `curves` and `curve_start_idx`.

The key distinction between `CurvilinearPolygon` and `Polygon` comes in their interaction with boolean operations. A `Polygon` can be differenced using `Clipper` (see `difference2d`), however a `CurvilinearPolygon` cannot directly. This is because `Clipper` will discretize the curved sections of a `CurvilinearPolygon`. This is particularly important for representing a geometry precisely for purposes of rendering to `SolidModel`.

See `CurvilinearRegion{T} <: GeometryEntity{T}` for the means of representing a difference operation between `CurvilinearPolygon`.
