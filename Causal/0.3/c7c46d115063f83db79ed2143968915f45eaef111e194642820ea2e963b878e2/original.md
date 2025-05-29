```julia
mutable struct DAESystem{RH, RO, ST<:(AbstractVector{<:Real}), SD<:(AbstractVector{<:Real}), DV<:(AbstractVector{<:Bool}), IP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}), OP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDAESystem
```

Constructs a generic DAE system.

# Example

```jldoctest
julia> function sfuncdae(out, dx, x, u, t)
           out[1] = x[1] + 1 - dx[1]
           out[2] = (x[1] + 1) * x[2] + 2
       end;

julia> ofuncdae(x, u, t) = x;

julia> x0 = [1., -1];

julia> dx0 = [2., 0.];

julia> DAESystem(righthandside=sfuncdae, readout=ofuncdae, state=x0, input=nothing, output=Outport(1), diffvars=[true, false], stateder=dx0)
DAESystem(righthandside:sfuncdae, readout:ofuncdae, state:[1.0, -1.0], t:0.0, input:nothing, output:Outport(numpins:1, eltype:Outpin{Float64}))
```
