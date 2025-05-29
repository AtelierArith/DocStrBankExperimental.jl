```
SecondOrderConstrainedDiscreteSystem
```

Discrete-time constrained second-order system of the form:

$$
    Mx_{k+2} + Cx_{k} + f_i(x_k) = f_e(t_k) \forall k, x_k ∈ X, f_e(t_k) ∈ U
$$

### Fields

  * `M`  – mass matrix
  * `C`  – viscosity matrix
  * `fi` – internal forces
  * `fe` – external forces
  * `X`  – state set
  * `U`  – input set
