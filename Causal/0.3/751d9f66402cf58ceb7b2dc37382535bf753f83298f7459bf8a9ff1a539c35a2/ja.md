```julia
struct SquarewaveGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

`SquarewaveGenerator`を次の形式の出力で構築します 

$$
    x(t) = \left\{\begin{array}{lr}
	A_1 + B, &  kT + \tau \leq t \leq (k + \alpha) T + \tau \\
	A_2 + B,  &  (k + \alpha) T + \tau \leq t \leq (k + 1) T + \tau	
	\end{array} \right. \quad k \in Z
$$

ここで、$A_1$, $A_2$は`level1`と`level2`、$T$は`period`、$\tau$は`delay`、$\alpha$は`duty`です。 

# フィールド

  * `high::Real`: 高レベル
  * `low::Real`: 低レベル
  * `period::Real`: 周期
  * `duty::Real`: デューティサイクル（範囲は(0, 1)）
  * `delay::Real`: 秒単位の遅延
  * `output::Causal.Outport`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
