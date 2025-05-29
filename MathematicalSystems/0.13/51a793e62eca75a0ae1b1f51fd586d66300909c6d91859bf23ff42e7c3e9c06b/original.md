```
SecondOrderContinuousSystem
```

Continuous-time second-order system of the form:

$$
    Mx''(t) + Cx'(t) + f_i(x) = f_e(t) \forall t
$$

### Fields

  * `M`  – mass matrix
  * `C`  – viscosity matrix
  * `fi` – internal forces
  * `fe` – external forces

### Notes

Typically `fi(x)` is a state-dependent function, and `fe` is a given vector. In this implementation, their respective types, `FI` and `FE`, are generic.
