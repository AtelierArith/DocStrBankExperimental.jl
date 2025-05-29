```
BlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

Discrete-time control system defined by a right-hand side of the form:

$$
    x_{k+1} = f(x_k, u_k) \; \forall k.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
