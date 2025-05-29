```
ConstrainedPolynomialDiscreteSystem
```

Discrete-time polynomial system with domain constraints:

$$
    x_{k+1} = p(x_k), \;  x_k ∈ \mathcal{X} \; \forall k.
$$

### Fields

  * `p`        – polynomial
  * `X`        – constraint set
  * `statedim` – number of state variables
