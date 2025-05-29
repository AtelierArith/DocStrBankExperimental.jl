```
ConstrainedLinearDescriptorContinuousSystem
```

Continuous-time linear system with domain constraints of the form:

$$
    E x(t)' = A x(t), \; x(t) ∈ \mathcal{X} \; \forall t.
$$

### Fields

  * `A` – state matrix
  * `E` – matrix, same size as `A`
  * `X` – state constraints
