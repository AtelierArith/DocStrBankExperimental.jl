```
struct StyleDict{S} <: GeometryEntityStyle where {S}
    styles::Dict{Vector{Int}, GeometryEntityStyle},
    default::S
end
```

Style used for applying differing styles to different Polygons at different levels within a `ClippedPolygon` or `CurvilinearRegion`. Styles are stored by the sequence of child indices required to find the corresponding `Clipper.PolyNode` within the `ClippedPolygon`. For a `CurvilinearRegion` only dictionaries of depth 2 (a single parent and one set of holes) are valid.
