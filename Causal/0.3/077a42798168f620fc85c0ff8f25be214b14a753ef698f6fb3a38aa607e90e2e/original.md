```julia
mutable struct DDESystem{CL, DL, RH, HST, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Inport, var"#s2876"<:Nothing}), OP<:(Union{var"#s2875", var"#s2874"} where {var"#s2875"<:Causal.Outport, var"#s2874"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDDESystem
```

Construct a generic DDE system 

# Fields

  * `constlags::Any`: Constant lags
  * `depslags::Any`: Dependent lags
  * `righthandside::Any`: Right-hand-side function
  * `history::Any`: History function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Inport, var"#s2876"<:Nothing}`: Input. Expected to be an `Inport` or `Nothing`
  * `output::Union{var"#s2875", var"#s2874"} where {var"#s2875"<:Causal.Outport, var"#s2874"<:Nothing}`: Output port
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
