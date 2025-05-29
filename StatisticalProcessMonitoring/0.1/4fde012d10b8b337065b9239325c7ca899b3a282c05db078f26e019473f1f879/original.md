```
MCUSUM(k, p, value = 0.0, St = zeros(p))
```

A Multivariate Cumulative Sum (MCUSUM) statistic.

### Arguments

  * `k::Float64`: The value of the allowance parameter.
  * `p::Int`: The number of variables to be monitored.
  * `value::Float64`: The initial value of the statistic. Default is 0.0.
  * `St::Vector{Float64}`: A vector representing the multivariate cumulative sum at the current time `t`.

### Examples

```
stat = MCUSUM(0.25, 2, 0.0, [0.0, 0.0])
```

### References

Crosier, R. B. (1988). Multivariate Generalizations of Cumulative Sum Quality-Control Schemes. Technometrics, 30(3), 291-303. https://doi.org/10.2307/1270083
