```
LLA(nodes::Dict{Int,ECEF}, datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

`ECEF` `nodes` の辞書を `LLA` 値の辞書に変換します。

**引数**

  * `nodes::Dict{Int,ECEF}` : ECEF ノードの辞書。
  * `datum::OpenStreetMapX.Ellipsoid` : 使用される楕円体のタイプ。
