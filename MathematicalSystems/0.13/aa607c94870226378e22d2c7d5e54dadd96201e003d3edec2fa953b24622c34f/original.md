```
ConstrainedBlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

Continuous-time control system defined by a right-hand side with domain constraints of the form:

$$
    x(t)' = f(x(t), u(t)), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
  * `X`        – state constraints
  * `U`        – input constraints
