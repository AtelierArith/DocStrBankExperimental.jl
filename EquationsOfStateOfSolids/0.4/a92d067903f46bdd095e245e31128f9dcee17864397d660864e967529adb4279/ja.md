```
PoirierTarantola2nd(v0, b0, e0=zero(v0 * b0))
```

ポワリエ–タラントラの二次状態方程式を作成します。

この状態方程式は単位を持つことができます。単位は[`Unitful.jl`](https://github.com/PainterQubits/Unitful.jl)の`@u_str`スタイルで指定されます。

# 引数

  * `v0`: ゼロ圧力での固体の体積。
  * `b0`: ゼロ圧力での固体の体積弾性率。
  * `e0`: ゼロ圧力での固体のエネルギー。
