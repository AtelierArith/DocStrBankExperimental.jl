```
intersection(geom1, geom2; gdataset=false)
```

### パラメータ

  * `geom1`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列であることができます。
  * `geom2`: 第二のジオメトリ。`geom1::AbstractGeometry`の場合はAbstractGeometry、または`geom1`がGMTタイプの場合はGMTdataset/行列です。

### キーワード

  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

ジオメトリの交差を表す新しいジオメトリを返します。交差がない場合やエラーが発生した場合はNULLを返します。

操作された2つのジオメトリの交差領域である新しいジオメトリを生成します。`intersects`関数を使用して、2つのジオメトリが交差するかどうかをテストできます。

### 返り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometryを返します。
