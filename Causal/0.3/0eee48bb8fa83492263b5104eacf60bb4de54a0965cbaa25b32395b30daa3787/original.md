```julia
mutable struct NoisyLorenzSystem{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, DR, DF, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Inport, var"#s2873"<:Nothing}), OP<:(Union{var"#s2872", var"#s2871"} where {var"#s2872"<:Causal.Outport, var"#s2871"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractSDESystem
```

Constructs a noisy Lorenz system 

# Fields

  * `σ::Real`: σ
  * `β::Real`: β
  * `ρ::Real`: ρ
  * `η::Real`: η
  * `γ::Real`: γ
  * `drift::Any`: Drift function
  * `diffusion::Any`: Diffusion function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Inport, var"#s2873"<:Nothing}`: Input. Expected to be an `Inport` or `Nothing`
  * `output::Union{var"#s2872", var"#s2871"} where {var"#s2872"<:Causal.Outport, var"#s2871"<:Nothing}`: Output port
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
