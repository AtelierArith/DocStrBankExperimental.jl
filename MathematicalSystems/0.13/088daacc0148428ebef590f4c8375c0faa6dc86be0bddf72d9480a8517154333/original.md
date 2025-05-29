```
NoisyConstrainedBlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

Continuous-time disturbance-affected control system defined by a right-hand side with domain constraints of the form:

$$
    x(t)' = f(x(t), u(t), w(t)), \quad x(t) ∈ \mathcal{X}, \quad u(t) ∈ \mathcal{U}, \quad w(t) ∈ \mathcal{W} \quad \forall t.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
  * `noisedim` – number of noise variables
  * `X`        – state constraints
  * `U`        – input constraints
  * `W`        – disturbance set
