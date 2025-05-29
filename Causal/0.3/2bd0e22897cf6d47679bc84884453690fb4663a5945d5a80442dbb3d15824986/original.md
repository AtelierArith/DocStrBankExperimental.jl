```julia
mutable struct ForcedChuaSystem{DT, T1<:Real, T2<:Real, T3<:Real, CM<:(AbstractMatrix{<:Real}), RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Inport, var"#s2873"<:Nothing}), OP<:(Union{var"#s2872", var"#s2871"} where {var"#s2872"<:Causal.Outport, var"#s2871"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

Constructs a Chua system with inputs.

# Fields

  * `diode::Any`: Chua diode. See [`PiecewiseLinearDiode`](@ref)
  * `α::Real`: α
  * `β::Real`: β
  * `γ::Real`: γ
  * `cplmat::AbstractMatrix{<:Real}`: Input coupling matrix. Expected to be a digonal matrix.
  * `righthandside::Any`: Right-hand-side matrix
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
