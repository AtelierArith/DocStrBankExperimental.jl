```
recgeo(rectan, re, f)
```

直交座標から測地座標に変換します。

### 引数

  * `rectan`: 点の直交座標
  * `re`: 基準楕円体の赤道半径
  * `f`: 扁平率

### 出力

  * `lon`: 点の測地経度（ラジアン）
  * `lat`: 点の測地緯度（ラジアン）
  * `alt`: 基準楕円体上の点の高度

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/recgeo_c.html)
