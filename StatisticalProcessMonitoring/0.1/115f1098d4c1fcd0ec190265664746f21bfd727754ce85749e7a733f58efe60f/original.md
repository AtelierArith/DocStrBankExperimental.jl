```
MAEWMA(λ, k, value, z::Vector{Float64})
```

A Multivariate Adaptive Exponentially Weighted Moving Average.

The update mechanism based on a new observation `x` is given by

$Z_t = (I-\Omega)\cdot Z_{t-1} + \Omega \cdot x_t$,

where $Ω = \omega(e)I_p$ is an adaptive generalization of the classical MEWMA smoothing matrix. The chart value is defined as

$value_t = Z_t' Z_t$.

### Arguments

  * `λ::Float64`: The value of the EWMA smoothing parameter.
  * `k::Float64`: The value of the parameter of the Huber score.
  * `value::Float64`: The value of the statistic. (default: `0.0`)
  * `z::Vector{Float64}`: The vector of smoothed observations.

### References

Mahmoud, M. A., & Zahran, A. R. (2010). A Multivariate Adaptive Exponentially Weighted Moving Average Control Chart. Communications in Statistics - Theory and Methods, 39(4), 606-625. https://doi.org/10.1080/03610920902755813
