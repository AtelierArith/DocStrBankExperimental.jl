```julia
mutable struct ForcedVanderpolSystem{T1<:Real, T2<:Real, CM<:(AbstractMatrix{<:Real}), RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}), OP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

Constructs a Vanderpol system driven by its input.

# Fields

  * `μ::Real`: μ
  * `γ::Real`: γ
  * `cplmat::AbstractMatrix{<:Real}`: Input coupling matrix. Expected to be a dioagonal matrix
  * `righthandside::Any`: Right-hand-side function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}`: Input. Expected to be an `Inport` or `Nothing`
  * `output::Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}`: Output port
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
