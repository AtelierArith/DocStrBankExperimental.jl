```julia
mutable struct BogdanovSystem{T1<:Real, T2<:Real, T3<:Real, T4<:Real, RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}), OP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDiscreteSystem
```

ボグダノフシステムを次の方程式で構築します

$$
\begin{array}{l}
    \dot{x}_1 = x_1 + \dot{x}_2 \\[0.25cm]
    \dot{x}_2 = x_2 + \epsilon + x_2 + k x_1 (x_1 - 1) + \mu  x_1 x_2
\end{array}
$$

# フィールド

  * `ε::Real`: ε
  * `μ::Real`: μ
  * `k::Real`: k
  * `γ::Real`: γ
  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}`: 入力。`Inport`または`Nothing`であることが期待されます
  * `output::Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}`: 出力ポート
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
