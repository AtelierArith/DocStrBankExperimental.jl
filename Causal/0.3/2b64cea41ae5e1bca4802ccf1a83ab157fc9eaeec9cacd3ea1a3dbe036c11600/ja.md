```julia
struct ConstantGenerator{T1<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

`ConstantGenerator`を次の形式の出力で構築します

$$
    x(t) = A
$$

ここで、$A$は`amplitude`です。

# フィールド

  * `amplitude::Real`: 振幅
  * `output::Causal.Outport`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
