```
frame(x)
```

ベクトル `x` が与えられたとき、このルーチンは右手系の直交基底 `x`、`y`、`z` を構築します。出力の `x` は入力の `x` に平行です。

### 引数

  * `x`: 入力ベクトル

### 出力

  * `x`: 出力の `x` に平行な単位ベクトル
  * `y`: `x` に直交する平面内の単位ベクトル
  * `z`: `x × y` によって与えられる単位ベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/frame_c.html)
