```julia
struct Differentiator{T1<:Real, T2<:Real, T3<:Real, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

`Differentiator`を構築します。入力出力関係は次の形式です。

$$
    y(t) = k_d \dot{u}(t)
$$

ここで、$u(t)$は入力、$y(t)$は出力、$kd$は微分定数です。

# フィールド

  * `kd::Real`: 微分ゲイン
  * `t::Real`: 時間
  * `u::Real`: 入力値
  * `input::Any`: 入力ポート
  * `output::Any`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
