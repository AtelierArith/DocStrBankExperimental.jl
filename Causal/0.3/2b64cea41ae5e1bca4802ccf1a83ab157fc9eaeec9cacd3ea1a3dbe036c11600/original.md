```julia
struct ConstantGenerator{T1<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a `ConstantGenerator` with output of the form

$$
    x(t) = A
$$

where $A$ is `amplitude.

# Fields

  * `amplitude::Real`: Amplitude
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
