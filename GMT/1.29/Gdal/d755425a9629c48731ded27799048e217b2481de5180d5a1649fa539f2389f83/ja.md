```
distance(geom1, geom2)
```

### パラメータ

  * `geom1`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列である可能性があります。
  * `geom2`: 第二のジオメトリ。`geom1::AbstractGeometry`の場合はAbstractGeometry、または`geom1`がGMTタイプの場合はGMTdataset/行列です。

ジオメトリ間の距離を返すか、エラーが発生した場合は-1を返します。
