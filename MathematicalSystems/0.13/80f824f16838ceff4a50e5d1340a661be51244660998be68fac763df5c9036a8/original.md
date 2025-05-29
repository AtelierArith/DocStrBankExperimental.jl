```
ConstrainedBlackBoxDiscreteSystem <: AbstractDiscreteSystem
```

Discrete-time system defined by a right-hand side with domain constraints of the form:

$$
    x_{k+1} = f(x_k), \; x_k ∈ \mathcal{X} \; \forall k.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `X`        – state constraints
