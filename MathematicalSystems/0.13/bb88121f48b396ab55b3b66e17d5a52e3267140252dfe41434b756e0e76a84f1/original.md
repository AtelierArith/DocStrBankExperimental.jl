```
ConstrainedDiscreteIdentitySystem <: AbstractDiscreteSystem
```

Trivial identity discrete-time system with domain constraints of the form:

$$
    x_{k+1} = x_k, \; x_k ∈ \mathcal{X} \; \forall k.
$$

### Fields

  * `statedim` – number of state variables
  * `X`        – state constraints
