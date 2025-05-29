```
NoisyConstrainedLinearContinuousSystem
```

Continuous-time linear system with  additive disturbance and domain constraints of the form:

$$
    x(t)' = A x(t) + D w(t), \; x(t) ∈ \mathcal{X}, \; w(t) ∈ \mathcal{W} \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `D` – noise matrix
  * `X` – state constraints
  * `W` – disturbance set
