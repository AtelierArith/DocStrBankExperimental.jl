```julia
mutable struct ODESystem{RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s1446", var"#s1445"} where {var"#s1446"<:Causal.Inport, var"#s1445"<:Nothing}), OP<:(Union{var"#s1444", var"#s1443"} where {var"#s1444"<:Causal.Outport, var"#s1443"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

Constructs a generic ODE system.

# Fields

  * `righthandside::Any`: Right-hand-side function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s1446", var"#s1445"} where {var"#s1446"<:Causal.Inport, var"#s1445"<:Nothing}`: Input. Expected to an `Inport` or `Nothing`
  * `output::Union{var"#s1444", var"#s1443"} where {var"#s1444"<:Causal.Outport, var"#s1443"<:Nothing}`: Output port
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

# Example

```jldoctest
julia> ds = ODESystem(righthandside=(dx,x,u,t)->(dx.=-x), readout=(x,u,t)->x, state=[1.],input=nothing, output=Outport(1));

julia> ds.state
1-element Array{Float64,1}:
 1.0
```
