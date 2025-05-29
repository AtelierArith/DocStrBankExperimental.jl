```julia
struct ExponentialGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs an `ExponentialGenerator` with output of the form

$$
    x(t) = A e^{\alpha (t - \tau)}
$$

where $A$ is `scale`, $\alpha$ is `decay` and $\tau$ is `delay`.

# Fields

  * `scale::Real`: Scale
  * `decay::Real`: Attenuation decay
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offset
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
