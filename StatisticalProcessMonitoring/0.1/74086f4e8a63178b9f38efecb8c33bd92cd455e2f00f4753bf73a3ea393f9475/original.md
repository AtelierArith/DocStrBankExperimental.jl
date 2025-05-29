```
AEWMA(λ, k, value)
```

Adaptive exponentially weighted moving average with design parameters `λ`, `k`, and initial value `value`.

The update mechanism for the statistic $C_t$ based on a new observation `x` is given by

$C_t = (1-\phi(e))\cdot C_{t-1} + \phi(e) \cdot x$,

where $\phi(e)$ is a forecast error function based on the Huber score function.

### Arguments

  * `λ::Float64`: The smoothing constant. Default is `0.1`.
  * `k::Float64`: The threshold value in the Huber score. Default is `3.0``.
  * `value::Float64`: The initial value of the statistic. Default is 0.0.

### References

Capizzi, G. & Masarotto, G. (2003). An Adaptive Exponentially Weighted Moving Average Control Chart. Technometrics, 45(3), 199-207.
