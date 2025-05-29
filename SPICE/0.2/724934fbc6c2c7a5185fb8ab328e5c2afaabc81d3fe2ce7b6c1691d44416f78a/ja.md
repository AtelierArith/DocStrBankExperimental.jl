```
latsph(radius, lon, lat)
```

緯度座標を球面座標に変換します。

### 引数

  * `radius`: 原点からの点の距離
  * `lon`: XZ平面からの点の角度（ラジアン）
  * `lat`: XY平面からの点の角度（ラジアン）

### 出力

タプル `(rho, colat, lons)` を返します。

  * `rho`: 原点からの点の距離
  * `colat`: 正のz軸からの点の角度（ラジアン）
  * `lons`: XZ平面からの点の角度（ラジアン）

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/latsph_c.html)
