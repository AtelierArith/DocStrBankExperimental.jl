```
ECEF(nodes::Dict{Int,ENU},lla_ref::LLA , datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

`ENU`ノードの辞書`nodes`を`ECEF`値の辞書に変換します。線形化のために参照点`lla_ref`を使用します。

**引数**

  * `nodes::Dict{Int,ENU},` : ENUノードの辞書。
  * `lla_ref::LLA` : 線形化のための参照点
  * `datum::OpenStreetMapX.Ellipsoid` : 使用される楕円体のタイプ。
