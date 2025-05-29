```julia
struct Terminator{IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

Constructs a `Terminator` with input bus `input`. The output function `g` is eqaul to `nothing`. A `Terminator` is used just  to sink the incomming data flowing from its `input`.

# Fields

  * `input::Any`: Input port
  * `output::Any`: Output. Must be nothing
  * `readout::Any`: Readout functionk. Must be nothing
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
