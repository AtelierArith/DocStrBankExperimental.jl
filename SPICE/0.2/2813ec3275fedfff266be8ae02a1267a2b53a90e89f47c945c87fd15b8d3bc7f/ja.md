```
dgeodr(x, y, z, re, f)
```

直交座標から測地座標への変換のヤコビアンを計算します。

### 引数

  * `x`: 点のX座標
  * `y`: 点のY座標
  * `z`: 点のZ座標
  * `re`: 基準楕円体の赤道半径
  * `f`: 扁平率

### 出力

部分導関数の行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dgeodr_c.html)
