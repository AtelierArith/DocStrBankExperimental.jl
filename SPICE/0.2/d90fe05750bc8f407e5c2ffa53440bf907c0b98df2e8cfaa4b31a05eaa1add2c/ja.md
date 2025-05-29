```
cylsph(r, lonc, z)
```

円柱座標から球座標への変換。

### 引数

  * `r`: z軸からの点の距離
  * `lonc`: XZ平面からの点の角度（ラジアン）
  * `z`: XY平面上の点の高さ

### 出力

  * `radius`: 原点からの点の距離
  * `colat`: 極角（ラジアンでの共緯度）
  * `lon`: 方位角（経度）

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/cylsph_c.html)
