```julia
struct DampedSinewaveGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, T6<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a `DampedSinewaveGenerator` which generates outputs of the form 

$$
    x(t) = A e^{\alpha t} sin(2 \pi f (t - \tau) + \phi) + B
$$

where $A$ is `amplitude`, $\alpha$ is `decay`, $f$ is `frequency`, $\phi$ is `phase`, $\tau$ is `delay`  and $B$ is `offset`.

# Fields

  * `amplitude::Real`: Amplitude
  * `decay::Real`: Attenuation rate
  * `frequency::Real`: Frequency
  * `phase::Real`: Phase
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offset
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout funtion
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
