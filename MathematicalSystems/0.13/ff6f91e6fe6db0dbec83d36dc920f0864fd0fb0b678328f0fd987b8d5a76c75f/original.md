```
NoisyConstrainedAffineControlContinuousSystem
```

Continuous-time affine control system with additive disturbance and domain constraints of the form:

$$
    x(t)' = A x(t) + B u(t) + c + D w(t), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U}, \; w(t) ∈ \mathcal{W} \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `c` – affine term
  * `D` – noise matrix
  * `X` – state constraints
  * `U` – input constraints
  * `W` – disturbance set
