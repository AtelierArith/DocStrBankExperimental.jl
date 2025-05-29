```
NoisyConstrainedBlackBoxControlDiscreteSystem <: AbstractDiscreteSystem
```

Discrete-time disturbance-affected control system defined by a right-hand side with domain constraints of the form:

$$
    x_{k+1} = f(x_k, u_k), \quad x_k ∈ \mathcal{X}, \quad u_k ∈ \mathcal{U}, \quad w_k ∈ \mathcal{W} \quad \forall k.
$$

### Fields

  * `f`        – function that holds the right-hand side
  * `statedim` – number of state variables
  * `inputdim` – number of input variables
  * `noisedim` – number of noise variables
  * `X`        – state constraints
  * `U`        – input constraints
  * `W`        – disturbance set
