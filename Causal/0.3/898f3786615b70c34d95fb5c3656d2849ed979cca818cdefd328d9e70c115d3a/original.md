```julia
struct FunctionGenerator{RO, OP<:Causal.Outport, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a generic function generator with `readout` function and `output` port.

# Fields

  * `readout::Any`: Readout function
  * `output::Causal.Outport`: Output port
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# Example

```jldoctest
julia> gen = FunctionGenerator(readout = t -> [t, 2t], output = Outport(2));

julia> gen.readout(1.)
2-element Array{Float64,1}:
 1.0
 2.0
```
