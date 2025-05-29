```
dpgrdr(x, y, z, re, f)
```

長方形座標から惑星地理座標への変換のヤコビ行列を計算します。

### 引数

  * `body`: 座標系に関連付けられた天体
  * `x`: 点のX座標
  * `y`: 点のY座標
  * `z`: 点のZ座標
  * `re`: 参照楕円体の赤道半径
  * `f`: 扁平率

### 出力

偏導関数の行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dpgrdr_c.html)
