```
struct CurvilinearPolygon{T} <: GeometryEntity{T}
    p::Vector{Point{T}}
    curves::Vector{<:Paths.Segment}
    curve_start_idx::Vector{Int}
end
```

座標のリストとそれらの間の曲線によって定義される曲線多角形。直線部分は暗黙的であり、任意の曲線は開始インデックスによって指定されます。`Polygon`は、空の`curves`と`curve_start_idx`を持つ`CurvilinearPolygon`を使用して表現できます。

`CurvilinearPolygon`と`Polygon`の主な違いは、ブール演算との相互作用にあります。`Polygon`は`Clipper`を使用して差分を取ることができます（`difference2d`を参照）、しかし`CurvilinearPolygon`は直接的にはできません。これは、`Clipper`が`CurvilinearPolygon`の曲がった部分を離散化するためです。これは、`SolidModel`にレンダリングする目的でジオメトリを正確に表現するために特に重要です。

`CurvilinearRegion{T} <: GeometryEntity{T}`を参照して、`CurvilinearPolygon`間の差分操作を表現する手段を確認してください。
