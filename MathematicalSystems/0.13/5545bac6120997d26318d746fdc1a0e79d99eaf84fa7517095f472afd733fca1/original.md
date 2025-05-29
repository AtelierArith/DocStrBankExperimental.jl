```
ConstrainedLinearDescriptorDiscreteSystem
```

Discrete-time linear system with domain constraints of the form:

$$
    E x_{k+1} = A x_k, \; x_k ∈ \mathcal{X} \; \forall k.
$$

### Fields

  * `A` – state matrix
  * `E` – matrix, same size as `A`
  * `X` – state constraints
