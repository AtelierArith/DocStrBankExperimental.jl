```
BlackBoxContinuousSystem <: AbstractContinuousSystem
```

Continuous-time system defined by a right-hand side of the form:

$$
    x(t)' = f(x(t)) \; \forall t.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
