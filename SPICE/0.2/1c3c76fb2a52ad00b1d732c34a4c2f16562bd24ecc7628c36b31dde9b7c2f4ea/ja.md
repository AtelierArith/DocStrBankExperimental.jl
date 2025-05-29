```
sphcyl(radius, colat, slon)
```

球面座標から円筒座標に変換します。

### 引数

  * `radius`: 原点からの点の距離
  * `colat`: 点の極角（ラジアン単位の共緯度）
  * `slon`: 点の方位角（経度）（ラジアン単位）

### 出力

  * `r`: Z軸からの点の距離
  * `lon`: XZ平面からの点の角度（ラジアン単位）
  * `z`: XY平面上の点の高さ

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sphcyl_c.html)
