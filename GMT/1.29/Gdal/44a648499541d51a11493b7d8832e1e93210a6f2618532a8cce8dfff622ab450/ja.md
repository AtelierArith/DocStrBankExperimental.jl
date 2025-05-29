```
concavehull(geom, ratio, allow_holes::Bool=true; gdataset=false)
```

### パラメータ

  * `geom`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列であることができます。
  * `ratio`: 凸包と凹包の面積の比率。
  * `allow_holes`: 穴を許可するかどうか。
  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometry。
