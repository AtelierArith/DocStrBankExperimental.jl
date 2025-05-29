```julia
mutable struct DelayFeedbackSystem{CL<:(AbstractVector{<:Real}), RH, HST, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}), OP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDDESystem
```

Constructs DelayFeedbackSystem

# Fields

  * `constlags::AbstractVector{<:Real}`: Constant lags
  * `depslags::Nothing`: Dependent lags
  * `righthandside::Any`: Right-hand-side function
  * `history::Any`: History function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}`: Input, Expected to be an `Inport` of `Nothing`
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
