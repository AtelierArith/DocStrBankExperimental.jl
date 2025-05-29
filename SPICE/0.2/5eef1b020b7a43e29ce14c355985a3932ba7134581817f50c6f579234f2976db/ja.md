```
oscelt(state, et, mu)
```

状態（位置、速度）に対応する接触円錐軌道要素のセットを決定します。

### 引数

  * `state`: 要素のエポックにおける天体の状態
  * `et`: 要素のエポック
  * `mu`: 主天体の重力パラメータ（GM）

### 出力

同等の円錐要素を返します：

  * `rp`: 周辺距離
  * `ecc`: 離心率
  * `inc`: 傾斜
  * `lnode`: 昇交点の経度
  * `argp`: 近日点引数
  * `m0`: エポックにおける平均異常
  * `t0`: エポック
  * `mu`: 重力パラメータ

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/oscelt_c.html)
