```
SecondOrderConstrainedAffineControlContinuousSystem
```

Continuous-time second order constrained affine control system of the form:

$$
    Mx''(t) + Cx'(t) + Kx(t) = Bu(t) + d, \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### Fields

  * `M` – mass matrix
  * `C` – viscosity matrix
  * `K` – stiffness matrix
  * `B` – input matrix
  * `d` – affine term
  * `X` – state constraints
  * `U` – input constraints
