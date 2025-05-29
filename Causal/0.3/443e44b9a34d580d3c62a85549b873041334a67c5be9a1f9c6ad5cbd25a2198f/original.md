```julia
struct StepGenerator{T1<:Real, T2<:Real, T3<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a `StepGenerator` with output of the form 

$$
    x(t) = \left\{\begin{array}{lr}
	B, &  t \leq \tau  \\
	A + B,  &  t > \tau
	\end{array} \right.
$$

where $A$ is `amplitude`, $B$ is the `offset` and $\tau$ is the `delay`.

# Fields

  * `amplitude::Real`: Amplitude
  * `delay::Real`: Delay in seconds
  * `offset::Real`: Offset
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
