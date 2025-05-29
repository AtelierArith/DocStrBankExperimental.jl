```
ConstrainedPolynomialContinuousSystem
```

Continuous-time polynomial system with domain constraints:

$$
    x(t)' = p(x(t)), \; x(t) ∈ \mathcal{X} \; \forall t.
$$

### Fields

  * `p`        – polynomial vector field
  * `X`        – constraint set
  * `statedim` – number of state variables
