```
ConstrainedAffineControlContinuousSystem
```

Continuous-time affine control system with domain constraints of the form:

$$
    x(t)' = A x(t) + B u(t) + c, \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `c` – affine term
  * `X` – state constraints
  * `U` – input constraints
