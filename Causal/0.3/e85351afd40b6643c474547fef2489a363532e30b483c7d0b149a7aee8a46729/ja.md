```julia
mutable struct HenonSystem{T1<:Real, T2<:Real, T3<:Real, RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Inport, var"#s2876"<:Nothing}), OP<:(Union{var"#s2875", var"#s2874"} where {var"#s2875"<:Causal.Outport, var"#s2874"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDiscreteSystem
```

`Henon` システムを構築し、次のダイナミクスで進化します。

$$
\begin{array}{l}
    \dot{x}_1 = 1 - \alpha (x_1^2) + x_2 \\[0.25cm]
    \dot{x}_2 = \beta x_1
\end{array}
$$

# フィールド

  * `α::Real`: α
  * `β::Real`: β
  * `γ::Real`: γ
  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Inport, var"#s2876"<:Nothing}`: 入力。`Inport` または `Nothing` であることが期待されます
  * `output::Union{var"#s2875", var"#s2874"} where {var"#s2875"<:Causal.Outport, var"#s2874"<:Nothing}`: 出力ポート
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

```
