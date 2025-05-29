```julia
mutable struct MultiplicativeNoiseLinearSystem{T1<:(AbstractMatrix{<:Real}), RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Inport, var"#s2877"<:Nothing}), OP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Outport, var"#s2875"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractRODESystem
```

`MultiplicativeNoiseLinearSystem`を次のダイナミクスで構築します。

$$
\begin{array}{l}
    \dot{x} = A x W
\end{array}
$$

ここで `W` はノイズプロセスです。

# フィールド

  * `A::AbstractMatrix{<:Real}`: A
  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Inport, var"#s2877"<:Nothing}`: 入力。`Inport`または`Nothing`であることが期待されます
  * `output::Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Outport, var"#s2875"<:Nothing}`: 出力ポート
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `t::Any`
  * `modelargs::Any`
  * `modelkwargs::Any`
  * `solverargs::Any`
  * `solverkwargs::Any`
  * `alg::Any`
  * `integrator::Any`
