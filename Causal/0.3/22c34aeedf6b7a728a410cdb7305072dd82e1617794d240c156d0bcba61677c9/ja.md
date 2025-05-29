```julia
struct DampedSinewaveGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, T6<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

`DampedSinewaveGenerator`を構築し、次の形式の出力を生成します。

$$
    x(t) = A e^{\alpha t} sin(2 \pi f (t - \tau) + \phi) + B
$$

ここで、$A$は`amplitude`、$\alpha$は`decay`、$f$は`frequency`、$\phi$は`phase`、$\tau$は`delay`、$B$は`offset`です。

# フィールド

  * `amplitude::Real`: 振幅
  * `decay::Real`: 減衰率
  * `frequency::Real`: 周波数
  * `phase::Real`: 位相
  * `delay::Real`: 秒単位の遅延
  * `offset::Real`: オフセット
  * `output::Causal.Outport`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
