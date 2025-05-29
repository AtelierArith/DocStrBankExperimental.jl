```
struct ClippedPolygon{T} <: AbstractPolygon{T}
    tree::Clipper.PolyNode{Point{T}}
end
```

Collection of polygons defined by a call to Clipper.
