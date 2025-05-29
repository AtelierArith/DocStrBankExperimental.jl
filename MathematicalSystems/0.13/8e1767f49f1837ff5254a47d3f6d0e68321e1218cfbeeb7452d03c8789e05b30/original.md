```
NoisyConstrainedLinearDiscreteSystem
```

Discrete-time linear system with additive disturbance and domain constraints of the form:

$$
    x_{k+1} = A x_k + D w_k, \; x_k ∈ \mathcal{X}, \; w(t) ∈ \mathcal{W} \; \forall k.
$$

### Fields

  * `A` – state matrix
  * `D` – noise matrix
  * `X` – state constraints
  * `W` – disturbance set
