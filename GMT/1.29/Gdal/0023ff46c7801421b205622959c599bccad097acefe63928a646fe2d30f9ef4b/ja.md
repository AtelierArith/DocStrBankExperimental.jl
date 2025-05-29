```
simplify(geom::AbstractGeometry, tol::Real; gdataset=false)
```

簡略化されたジオメトリを計算します。

### パラメータ

  * `geom`: ジオメトリ。
  * `tol`: 簡略化のための距離許容値。

### キーワード

  * `gdataset`: 入力がGMTdatasetまたはMatrixであってもGDAL IGeometryを返します。
