```
polyunion(geom1, geom2; gdataset=false)
```

幾何の和を表す新しい幾何を計算します。

### パラメータ

  * `geom1`: 幾何。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列であることができます。
  * `geom2`: 第二の幾何。`geom1::AbstractGeometry`の場合はAbstractGeometry、または`geom1`がGMTタイプの場合はGMTdataset/行列です。

### キーワード

  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometryを返します。
