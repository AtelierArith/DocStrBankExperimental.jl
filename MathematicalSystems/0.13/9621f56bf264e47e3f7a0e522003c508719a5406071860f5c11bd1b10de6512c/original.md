```
NoisyConstrainedLinearControlContinuousSystem
```

Continuous-time linear control system with additive disturbance and domain constraints of the form:

$$
    x(t)' = A x(t) + B u(t) + D w(t), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U}, \; w(t) ∈ \mathcal{W} \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `D` – noise matrix
  * `X` – state constraints
  * `U` – input constraints
  * `W` – disturbance set
