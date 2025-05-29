```julia
struct Differentiator{T1<:Real, T2<:Real, T3<:Real, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

Consructs a `Differentiator` whose input output relation is of the form 

$$
    y(t) = k_d \dot{u}(t)
$$

where $u(t)$ is the input and $y(t)$ is the output and $kd$ is the differentiation constant.

# Fields

  * `kd::Real`: Differentiation gain
  * `t::Real`: Time
  * `u::Real`: Input value
  * `input::Any`: Input port
  * `output::Any`: Output port
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
