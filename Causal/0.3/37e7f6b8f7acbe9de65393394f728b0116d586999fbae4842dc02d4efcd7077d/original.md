```julia
mutable struct SDESystem{DR, DF, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2879", var"#s2878"} where {var"#s2879"<:Causal.Inport, var"#s2878"<:Nothing}), OP<:(Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Outport, var"#s2876"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractSDESystem
```

Constructs a SDE system. 

# Fields

  * `drift::Any`: Drift function
  * `diffusion::Any`: diffusion function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2879", var"#s2878"} where {var"#s2879"<:Causal.Inport, var"#s2878"<:Nothing}`: Input. Expected to be an `Inport` or `Nothing`
  * `output::Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Outport, var"#s2876"<:Nothing}`: Output port
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
