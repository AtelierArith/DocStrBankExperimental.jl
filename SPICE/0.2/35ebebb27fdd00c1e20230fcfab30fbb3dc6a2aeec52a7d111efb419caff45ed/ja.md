```
recpgr(body, rectan, re, f)
```

長方形座標を惑星地理座標に変換します。

### 引数

  * `body`: 座標系に関連付けられた天体
  * `rectan`: 点の長方形座標
  * `re`: 参照楕円体の赤道半径
  * `f`: 平坦化係数

### 出力

  * `lon`: 点の惑星地理的経度（ラジアン）。
  * `lat`: 点の惑星地理的緯度（ラジアン）。
  * `alt`: 参照楕円体上の点の高度。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/recpgr_c.html)
