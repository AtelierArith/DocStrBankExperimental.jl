```
pointalongline(geom, distance::Real; gdataset=false)
```

### パラメータ

  * `geom`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列である可能性があります。
  * `distance`: 曲線に沿った位置をサンプリングする距離。この距離は、曲線のgeomlength()の間である必要があります。
  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

曲線に沿った指定された距離で点（またはNULL）を取得します。

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometry。
