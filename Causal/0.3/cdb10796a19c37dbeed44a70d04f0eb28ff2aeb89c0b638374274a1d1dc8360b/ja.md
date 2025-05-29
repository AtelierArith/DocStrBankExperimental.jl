```julia
mutable struct DiscreteSystem{RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2880", var"#s2879"} where {var"#s2880"<:Causal.Inport, var"#s2879"<:Nothing}), OP<:(Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Outport, var"#s2877"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDiscreteSystem
```

一般的な離散システム

# フィールド

  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2880", var"#s2879"} where {var"#s2880"<:Causal.Inport, var"#s2879"<:Nothing}`: 入力。`Inport`または`Nothing`であることが期待されます
  * `output::Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Outport, var"#s2877"<:Nothing}`: 出力ポート
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

# 例

```jldoctest
julia> sfuncdiscrete(dx,x,u,t) = (dx .= 0.5x);

julia> ofuncdiscrete(x, u, t) = x;

julia> DiscreteSystem(righthandside=sfuncdiscrete, readout=ofuncdiscrete, state=[1.], input=nothing, output=Outport())
DiscreteSystem(righthandside:sfuncdiscrete, readout:ofuncdiscrete, state:[1.0], t:0.0, input:nothing, output:Outport(numpins:1, eltype:Outpin{Float64}))

```
