```julia
struct StepGenerator{T1<:Real, T2<:Real, T3<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

`StepGenerator`を次の形式の出力で構築します 

$$
    x(t) = \left\{\begin{array}{lr}
	B, &  t \leq \tau  \\
	A + B,  &  t > \tau
	\end{array} \right.
$$

ここで、$A$は`amplitude`、$B$は`offset`、$\tau$は`delay`です。

# フィールド

  * `amplitude::Real`: 振幅
  * `delay::Real`: 秒単位の遅延
  * `offset::Real`: オフセット
  * `output::Causal.Outport`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
