```
SecondOrderDiscreteSystem
```

Discrete-time second-order system of the form:

$$
    Mx_{k+2} + Cx_{k} + f_i(x_k) = f_e(t_k) \forall k.
$$

### Fields

  * `M`  – mass matrix
  * `C`  – viscosity matrix
  * `fi` – internal forces
  * `fe` – external forces

### Notes

Typically `fi(x_k)` is a state-dependent function, and `fe` is a given vector. In this implementation, their respective types, `FI` and `FE`, are generic.
