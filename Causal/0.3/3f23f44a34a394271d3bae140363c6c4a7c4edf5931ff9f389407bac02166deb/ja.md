```julia
mutable struct GingerbreadmanSystem{T1<:Real, RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2879", var"#s2878"} where {var"#s2879"<:Causal.Inport, var"#s2878"<:Nothing}), OP<:(Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Outport, var"#s2876"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDiscreteSystem
```

GingerbreadmanSystemを次のダイナミクスで構築します。

$$
\begin{array}{l}
    \dot{x}_1 = 1 - x_2 + |x_1|\\[0.25cm]
    \dot{x}_2 = x_1
\end{array}
$$

# フィールド

  * `γ::Real`: γ
  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2879", var"#s2878"} where {var"#s2879"<:Causal.Inport, var"#s2878"<:Nothing}`: 入力。`Inport`または`Nothing`であることが期待されます
  * `output::Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Outport, var"#s2876"<:Nothing}`: 出力ポート
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
