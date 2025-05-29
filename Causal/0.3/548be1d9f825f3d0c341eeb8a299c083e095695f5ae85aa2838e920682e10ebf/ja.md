```julia
mutable struct ForcedNoisyLorenzSystem{T1<:Real, T2<:Real, T3<:Real, T4<:Real, CM<:(AbstractMatrix{<:Real}), T5<:Real, DR, DF, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2872", var"#s2871"} where {var"#s2872"<:Causal.Inport, var"#s2871"<:Nothing}), OP<:(Union{var"#s2870", var"#s2869"} where {var"#s2870"<:Causal.Outport, var"#s2869"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractSDESystem
```

ノイズのあるローレンツシステムを構築します

# フィールド

  * `σ::Real`: σ
  * `β::Real`: β
  * `ρ::Real`: ρ
  * `η::Real`: η
  * `cplmat::AbstractMatrix{<:Real}`: 入力結合行列。対角行列であることが期待されます。
  * `γ::Real`: γ
  * `drift::Any`: ドリフト関数
  * `diffusion::Any`: 拡散関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2872", var"#s2871"} where {var"#s2872"<:Causal.Inport, var"#s2871"<:Nothing}`: 入力。`Inport`または`Nothing`であることが期待されます。
  * `output::Union{var"#s2870", var"#s2869"} where {var"#s2870"<:Causal.Outport, var"#s2869"<:Nothing}`: 出力ポート
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
