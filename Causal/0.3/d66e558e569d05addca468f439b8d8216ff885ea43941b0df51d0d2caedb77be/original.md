```julia
mutable struct RODESystem{RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2880", var"#s2879"} where {var"#s2880"<:Causal.Inport, var"#s2879"<:Nothing}), OP<:(Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Outport, var"#s2877"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractRODESystem
```

Constructs a generic RODE system 

# Fields

  * `righthandside::Any`: Right-hand-side function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2880", var"#s2879"} where {var"#s2880"<:Causal.Inport, var"#s2879"<:Nothing}`: Input. Expected to be an `Inport` or `Nothing`
  * `output::Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Outport, var"#s2877"<:Nothing}`: Output port
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
