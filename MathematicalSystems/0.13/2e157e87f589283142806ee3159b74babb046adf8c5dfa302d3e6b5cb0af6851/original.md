```
NoisyAffineControlContinuousSystem
```

Continuous-time affine control system with additive disturbance of the form:

$$
    x(t)' = A x(t) + B u(t) + c + D w(t) \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `c` – affine term
  * `D` – noise matrix
