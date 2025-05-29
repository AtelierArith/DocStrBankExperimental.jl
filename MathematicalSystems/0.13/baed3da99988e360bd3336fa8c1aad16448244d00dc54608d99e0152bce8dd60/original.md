```
ConstrainedAffineControlDiscreteSystem
```

Continuous-time affine control system with domain constraints of the form:

$$
    x_{k+1} = A x_k + B u_k + c, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U} \; \forall k.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `c` – affine term
  * `X` – state constraints
  * `U` – input constraints
