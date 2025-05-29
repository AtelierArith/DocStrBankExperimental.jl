```
delaunay(geom::AbstractGeometry, tol::Real=0, onlyedges::Bool=true; gdataset=false)
```

### パラメータ

  * `geom`: ジオメトリ。
  * `tol`: 改善された堅牢性のために使用するオプションのスナッピングトレランス
  * `onlyedges`: `true` の場合、MULTILINESTRINGを返します。それ以外の場合は、三角形のPOLYGONを含むGEOMETRYCOLLECTIONを返します。
  * `gdataset`: 入力がGMTdatasetまたはMatrixであっても、GDAL IGeometryを返します

ジオメトリの頂点のデローニ三角形分割を返します。
