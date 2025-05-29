```
ConstrainedContinuousIdentitySystem <: AbstractContinuousSystem
```

Trivial identity continuous-time system with domain constraints of the form:

$$
    x(t)' = 0, \; x(t) ∈ \mathcal{X} \; \forall t.
$$

### Fields

  * `statedim` – number of state variables
  * `X`        – state constraints
