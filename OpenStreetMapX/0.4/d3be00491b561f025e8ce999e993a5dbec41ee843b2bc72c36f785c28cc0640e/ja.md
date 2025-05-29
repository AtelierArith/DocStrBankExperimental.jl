```
ECEF(enu::ENU, lla_ref::LLA, datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

与えられた `enu` 座標から、線形化のための参照点 `lla_ref` を使用して ECEF 座標を作成します。

**引数**

  * `enu::enu` : 使用される座標
  * `lla_ref::LLA` : 線形化のための参照点
  * `datum::OpenStreetMapX.Ellipsoid` : 使用される楕円体のタイプ。
