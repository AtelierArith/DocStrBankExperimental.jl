```julia
struct RampGenerator{T1<:Real, T2<:Real, T3<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a `RampGenerator` with output of the form

$$
    x(t) = \alpha (t - \tau)
$$

where $\alpha$ is the `scale` and $\tau$ is `delay`.

# Fields

  * `scale::Real`: Scale
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offset
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
