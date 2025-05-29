```
latcyl(radius, lon, lat)
```

緯度座標を円筒座標に変換します。

### 引数

  * `radius`: 原点からの点の距離
  * `lon`: XZ平面からの点の角度（ラジアン）
  * `lat`: XY平面からの点の角度（ラジアン）

### 出力

タプル `(r, lonc, z)` を返します。

  * `r`: z軸からの点の距離
  * `lonc`: XZ平面からの点の角度（ラジアン）。'lonc' は 'lon' と等しく設定されます
  * `z`: XY平面上の点の高さ

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/latcyl_c.html)
