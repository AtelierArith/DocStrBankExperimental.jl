```
exp_underapproximation(A::IntervalMatrix{T}, t, p) where {T}
```

区間行列の指数関数の下近似、`exp(A*t)`、を切り捨てたテイラー級数展開を使用して行います。

### 入力

  * `A` – 区間行列
  * `t` – 指数化因子
  * `p` – 近似の次数

### 出力

`exp(A*t)`の下近似、すなわち`M = (m_{ij})`という区間行列で、`m_{ij} ⊆ [exp(A*t)]_{ij}`となるもの。

### アルゴリズム

M. Althoff, O. Stursberg, M. Bussによる*不確実なパラメータと入力を持つ線形システムの到達可能性解析*の定理2を参照してください。
