```
GeoRegion
```

地理的地域のための抽象スーパタイプ。すべての `GeoRegion` タイプは以下のフィールドを含みます：

  * `ID` - GeoRegionの識別子である `String` タイプ。
  * `pID` - 親GeoRegionの識別子である `String` タイプ。
  * `name` - GeoRegionのフルネームである `String` タイプ。
  * `bound` - GeoRegionの境界を定義する `Float` タイプのベクトル [北, 南, 東, 西]。
  * `shape` - GeoRegionの非直線的な形状を定義する `Point2` (参照：[GeometryBasics.jl](https://github.com/JuliaGeometry/GeometryBasics.jl)) タイプのベクトル。
  * `geometry` - 多角形のチェックを行う際に便利な `Polygon` タイプ (参照：[GeometryBasics.jl](https://github.com/JuliaGeometry/GeometryBasics.jl))、および [GeometryOps.jl](https://github.com/JuliaGeo/GeometryOps.jl) を使用します。
