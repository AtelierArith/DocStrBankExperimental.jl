```
drdpgr(body, lon, lat, alt, re, f)
```

惑星地理座標から直交座標への変換のヤコビ行列を計算します。

### 引数

  * `body`: 座標に関連付けられた天体の名前
  * `lon`: 点の惑星地理的経度（ラジアン）
  * `lat`: 点の惑星地理的緯度（ラジアン）
  * `alt`: 基準楕円体上の点の高度
  * `re`: 基準楕円体の赤道半径
  * `f`: 扁平率

### 出力

偏微分の行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdpgr_c.html)
