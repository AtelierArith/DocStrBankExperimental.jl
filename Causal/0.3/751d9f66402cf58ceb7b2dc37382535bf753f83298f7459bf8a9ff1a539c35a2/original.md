```julia
struct SquarewaveGenerator{T1<:Real, T2<:Real, T3<:Real, T4<:Real, T5<:Real, OP<:Causal.Outport, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

Constructs a `SquarewaveGenerator` with output of the form 

$$
    x(t) = \left\{\begin{array}{lr}
	A_1 + B, &  kT + \tau \leq t \leq (k + \alpha) T + \tau \\
	A_2 + B,  &  (k + \alpha) T + \tau \leq t \leq (k + 1) T + \tau	
	\end{array} \right. \quad k \in Z
$$

where $A_1$, $A_2$ is `level1` and `level2`, $T$ is `period`, $\tau$ is `delay` $\alpha$ is `duty`. 

# Fields

  * `high::Real`: High level
  * `low::Real`: Low level
  * `period::Real`: Period
  * `duty::Real`: Duty cycle given in range (0, 1)
  * `delay::Real`: Delay in seconds
  * `output::Causal.Outport`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
