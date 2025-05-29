```
drdgeo(lon, lat, alt, re, f)
```

緯度経度から直交座標への変換のヤコビ行列を計算します。

### 引数

  * `lon`: 点の測地経度（ラジアン）
  * `lat`: 点の測地緯度（ラジアン）
  * `alt`: 基準楕円体上の点の高度
  * `re`: 基準楕円体の赤道半径
  * `f`: 扁平率

### 出力

偏微分の行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdgeo_c.html)
