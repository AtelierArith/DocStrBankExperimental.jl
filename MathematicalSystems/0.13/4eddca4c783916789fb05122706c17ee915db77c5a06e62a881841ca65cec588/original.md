```
ConstrainedBlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

Discrete-time control system defined by a right-hand side with domain constraints of the form:

$$
    x_{k+1} = f(x_k, u_k), \; x_k ∈ \mathcal{X}, \;  u_k ∈ \mathcal{U} \; \forall k.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
  * `X`        – state constraints
  * `U`        – input constraints
