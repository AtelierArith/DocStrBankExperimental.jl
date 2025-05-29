```
NoisyConstrainedAffineControlDiscreteSystem
```

Continuous-time affine control system with additive disturbance and domain constraints of the form:

$$
    x_{k+1} = A x_k + B u_k + c + D w_k, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U}, \; w_k ∈ \mathcal{W} \; \forall k.
$$

### Fields

  * `A` – state matrix
  * `B` – input matrix
  * `c` – affine term
  * `D` – noise matrix
  * `X` – state constraints
  * `U` – input constraints
  * `W` – disturbance set
