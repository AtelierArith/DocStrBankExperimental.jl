```
NoisyBlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

Continuous-time disturbance-affected control system defined by a right-hand side of the form:

$$
    x(t)' = f(x(t), u(t), w(t)) \; \forall t.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
  * `noisedim` – number of noise variables
