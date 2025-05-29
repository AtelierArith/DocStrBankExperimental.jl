```
SecondOrderConstrainedLinearControlDiscreteSystem
```

Discrete-time second order constrained linear control system of the form:

$$
    Mx_{k+2} + Cx_{k+1} + Kx_k = Bu_k, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U} \; \forall k.
$$

### Fields

  * `M` – mass matrix
  * `C` – viscosity matrix
  * `K` – stiffness matrix
  * `B` – input matrix
  * `X` – state constraints
  * `U` – input constraints
