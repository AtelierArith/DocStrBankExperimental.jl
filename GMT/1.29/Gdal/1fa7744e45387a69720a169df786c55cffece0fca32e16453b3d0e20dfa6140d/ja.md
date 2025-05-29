```
intersects(geom1, geom2)
```

### パラメータ

  * `geom1`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列である可能性があります。
  * `geom2`: 第二のジオメトリ。`geom1::AbstractGeometry`の場合はAbstractGeometry、または`geom1`がGMTタイプの場合はGMTdataset/行列です。

ジオメトリが交差するかどうかを返します。

2つのジオメトリが交差するかどうかを判断します。GEOSが有効な場合、これは厳密な方法で行われます。それ以外の場合、2つのジオメトリのエンベロープ（バウンディングボックス）が重なる場合は`true`が返されます。
