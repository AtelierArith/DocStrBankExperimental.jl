```
struct CurvilinearRegion{T} <: GeometryEntity{T}
    exterior::CurvilinearPolygon{T}
    holes::Vector{CurvilinearPolygon{T}}
end
```

外部の `CurvilinearPolygon{T}` とオプションの内部の穴で構成される曲線領域 `CurvilinearRegion{T}`。これらの穴は互いに、また外部と交差することはできません。
