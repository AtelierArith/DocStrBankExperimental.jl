```
ConstrainedBlackBoxContinuousSystem <: AbstractContinuousSystem
```

Continuous-time system defined by a right-hand side with domain constraints of the form:

$$
    x(t)' = f(x(t)), \; x(t) ∈ \mathcal{X} \; \forall t.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `X`        – state constraints
