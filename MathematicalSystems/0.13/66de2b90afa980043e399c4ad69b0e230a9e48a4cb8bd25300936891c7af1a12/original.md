```
NoisyAffineControlDiscreteSystem
```

Continuous-time affine control system with additive disturbance of the form:

$$
    x_{k+1} = A x_k + B u_k + c + D w_k \; \forall k.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `c` – affine term
  * `D` – noise matrix
