```julia
struct StaticSystem{RO, IP, OP, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

Consructs a generic static system with `readout` function, `input` port and `output` port.

# Fields

  * `readout::Any`: Readout function
  * `input::Any`: Input port
  * `output::Any`: Output. May be an `Outport` of `Nothing`
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# Example

```jldoctest
julia> ss = StaticSystem(readout = (t,u) -> u[1] + u[2], input=Inport(2), output=Outport(1));

julia> ss.readout(0., ones(2))
2.0
```
