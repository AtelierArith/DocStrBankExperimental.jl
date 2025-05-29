```
NoisyBlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

Discrete-time disturbance-affected control system defined by a right-hand side of the form:

$$
    x_{k+1} = f(x_k, u_k) \quad \forall k.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
  * `noisedim` – number of noise variables
