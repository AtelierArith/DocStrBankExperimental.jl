```
struct CurvilinearRegion{T} <: GeometryEntity{T}
    exterior::CurvilinearPolygon{T}
    holes::Vector{CurvilinearPolygon{T}}
end
```

A curvilinear region made up of an exterior::CurvilinearPolygon{T} and optional interior holes made up of CurvilinearPolygon{T}. These holes cannot intersect each other or the exterior.
