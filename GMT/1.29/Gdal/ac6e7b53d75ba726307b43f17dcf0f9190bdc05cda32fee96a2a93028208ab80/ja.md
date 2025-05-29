```
difference(geom1, geom2; gdataset=false)
```

### パラメータ

  * `geom1`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列であることができます。
  * `geom2`: 第二のジオメトリ。`geom1::AbstractGeometry`の場合はAbstractGeometry、または`geom1`がGMTタイプの場合はGMTdataset/行列です。

### キーワード

  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

このジオメトリの領域から他のジオメトリの領域を除去した新しいジオメトリを生成します。

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometryを返します。
