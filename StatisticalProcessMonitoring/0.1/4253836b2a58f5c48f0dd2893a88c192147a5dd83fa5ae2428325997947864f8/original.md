```
EWMA(λ, value)
```

Exponentially weighted moving average with design parameter `λ` and initial value `value`.

The update mechanism for the statistic $C_t$ based on a new observation `x` is given by

$C_t = (1-λ)\cdot C_{t-1} + λ \cdot x$.

### Arguments

  * `λ::Float64`: The smoothing constant. Defaults to `0.1`.
  * `value::Float64`: The initial value for the EWMA statistic. Defaults to `0.0`.

### References

Roberts, S. W. (1959). Control Chart Tests Based on Geometric Moving Averages. Technometrics, 1(3), 239-250. https://doi.org/10.1080/00401706.1959.10489860
