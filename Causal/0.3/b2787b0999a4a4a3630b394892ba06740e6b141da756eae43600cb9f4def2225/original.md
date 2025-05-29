```julia
struct DampedExponentialGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs an `DampedExponentialGenerator` with outpsuts of the form 

$$
    x(t) = A (t - \tau) e^{\alpha (t - \tau)}
$$

where $A$ is `scale`, $\alpha$ is `decay`, $\tau$ is `delay`.

# Fields

  * `scale::Real`: Scale
  * `decay::Real`: Attenuation rate
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offet
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Reaodout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
