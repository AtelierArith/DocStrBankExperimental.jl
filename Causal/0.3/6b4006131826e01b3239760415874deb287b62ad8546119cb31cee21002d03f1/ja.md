```julia
struct Coupler{C1, C2, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

接続行列 `conmat` のサイズが $n \times n$ で、結合行列 `cplmat` のサイズが $d \times d$ のカプラーを構築します。`Coupler` の出力関数 `g` は次の形をしています。

$$
    y = g(u, t) = (E \otimes P) u
$$

ここで、$\otimes$ はクロネッカー積、$E$ は `conmat`、$P$ は `cplmat`、$u$ は `input` の値、$y$ は `output` の値です。

# フィールド

  * `conmat::Any`: 外部結合行列
  * `cplmat::Any`: 内部結合行列
  * `input::Any`: 入力ポート
  * `output::Any`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
