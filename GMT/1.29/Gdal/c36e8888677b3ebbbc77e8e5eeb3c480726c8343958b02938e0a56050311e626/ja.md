```
convexhull(geom; gdataset=false)
```

### パラメータ

  * `geom`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列であることができます。
  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

メソッドが呼び出されたジオメトリの凸包を含む新しいジオメトリオブジェクトが作成され、返されます。

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometry。
