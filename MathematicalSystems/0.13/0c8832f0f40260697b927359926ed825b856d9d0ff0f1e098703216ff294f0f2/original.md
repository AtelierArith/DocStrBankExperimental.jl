```
BlackBoxDiscreteSystem <: AbstractDiscreteSystem
```

Discrete-time system defined by a right-hand side of the form:

$$
    x_{k+1} = f(x_k) \; \forall k.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
