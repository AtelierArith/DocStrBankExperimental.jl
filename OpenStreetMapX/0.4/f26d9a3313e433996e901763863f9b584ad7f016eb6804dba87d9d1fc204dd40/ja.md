```
ECEF(nodes::Dict{Int,LLA}, datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

`LLA` `nodes` の辞書を `ECEF` 値の辞書に変換します。線形化のために参照点 `lla_ref` を使用します。

**引数**

  * `nodes::Dict{Int,LLA}` : LLA ノードの辞書。
  * `datum::OpenStreetMapX.Ellipsoid` : 使用される楕円体のタイプ。
