```
SecondOrderConstrainedLinearControlContinuousSystem
```

Continuous-time second order constrained linear control system of the form:

$$
    Mx''(t) + Cx'(t) + Kx(t) = Bu(t), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### Fields

  * `M` – mass matrix
  * `C` – viscosity matrix
  * `K` – stiffness matrix
  * `B` – input matrix
  * `X` – state constraints
  * `U` – input constraints
