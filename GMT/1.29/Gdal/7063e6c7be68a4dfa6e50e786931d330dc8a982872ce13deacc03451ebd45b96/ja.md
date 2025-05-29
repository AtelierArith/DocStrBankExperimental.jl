```
overlaps(geom1, geom2)
```

### パラメータ

  * `geom1`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列である可能性があります。
  * `geom2`: 第二のジオメトリ。`geom1::AbstractGeometry`の場合はAbstractGeometry、または`geom1`がGMTタイプの場合はGMTdataset/行列です。

ジオメトリが重なっている場合は`true`を返します。
