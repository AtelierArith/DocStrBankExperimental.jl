```julia
struct TriangularwaveGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a `TriangularwaveGenerator` with output of the form

$$
    x(t) = \left\{\begin{array}{lr}
	\dfrac{A t}{\alpha T} + B, &  kT + \tau \leq t \leq (k + \alpha) T + \tau \\[0.25cm]
	\dfrac{A (T - t)}{T (1 - \alpha)} + B,  &  (k + \alpha) T + \tau \leq t \leq (k + 1) T + \tau	
	\end{array} \right. \quad k \in Z
$$

where $A$ is `amplitude`, $T$ is `period`, $\tau$ is `delay` $\alpha$ is `duty`. 

# Fields

  * `amplitude::Real`: Amplitude
  * `period::Real`: Period
  * `duty::Real`: Duty cycle
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offset
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
