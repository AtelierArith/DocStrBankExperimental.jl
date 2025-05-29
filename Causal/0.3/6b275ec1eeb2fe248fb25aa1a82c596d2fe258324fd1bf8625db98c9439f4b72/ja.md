```julia
struct TriangularwaveGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

`TriangularwaveGenerator`を次の形式の出力で構築します

$$
    x(t) = \left\{\begin{array}{lr}
	\dfrac{A t}{\alpha T} + B, &  kT + \tau \leq t \leq (k + \alpha) T + \tau \\[0.25cm]
	\dfrac{A (T - t)}{T (1 - \alpha)} + B,  &  (k + \alpha) T + \tau \leq t \leq (k + 1) T + \tau	
	\end{array} \right. \quad k \in Z
$$

ここで、$A$は`amplitude`、$T$は`period`、$\tau$は`delay`、$\alpha$は`duty`です。

# フィールド

  * `amplitude::Real`: 振幅
  * `period::Real`: 周期
  * `duty::Real`: デューティサイクル
  * `delay::Real`: 秒単位の遅延
  * `offset::Real`: オフセット
  * `output::Causal.Outport`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

```
