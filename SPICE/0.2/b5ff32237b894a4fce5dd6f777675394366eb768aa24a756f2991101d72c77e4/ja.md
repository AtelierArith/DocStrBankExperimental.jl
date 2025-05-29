```
pgrrec(body, lon, lat, alt, re, f)
```

惑星座標を直交座標に変換します。

### 引数

  * `body`: 座標系に関連付けられた天体。
  * `lon`: 点の惑星経度（ラジアン）。
  * `lat`: 点の惑星緯度（ラジアン）。
  * `alt`: 基準楕円体上の点の高度。
  * `re`: 基準楕円体の赤道半径。
  * `f`: 扁平率。

### 出力

点の直交座標を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pgrrec_c.html)
