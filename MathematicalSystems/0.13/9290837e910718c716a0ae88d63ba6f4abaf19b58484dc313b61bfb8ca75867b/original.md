```
ConstrainedLinearControlContinuousSystem
```

Continuous-time linear control system with domain constraints of the form:

$$
    x(t)' = A x(t) + B u(t), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `X` – state constraints
  * `U` – input constraints
