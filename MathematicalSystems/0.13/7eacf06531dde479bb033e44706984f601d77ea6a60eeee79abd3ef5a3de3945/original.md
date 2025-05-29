```
SecondOrderConstrainedContinuousSystem
```

Continuous-time constrained second-order system of the form:

$$
    Mx''(t) + Cx'(t) + f_i(x) = f_e(t) \forall t, x ∈ X, f_e(t) ∈ U
$$

### Fields

  * `M`  – mass matrix
  * `C`  – viscosity matrix
  * `fi` – internal forces
  * `fe` – external forces
  * `X`  – state set
  * `U`  – input set
