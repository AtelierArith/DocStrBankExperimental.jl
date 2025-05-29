```
AMCUSUM(λ, p; minshift = 0.1, shift = 0.0, Et = zeros(p), t = 0, stat = MCUSUM(k=0.1, p=p))
```

An Adaptive Multivariate Cumulative Sum (MCUSUM) statistic.

### Arguments

  * `λ::Float64`: The smoothing constant, such that 0.0 <= λ <= 1.0.
  * `p::Int`: The number of quality variables to monitor.
  * `minshift::Float64`: The minimum shift value to be detected. Default is 0.1.
  * `shift::Float64`: The current shift value. Default is 0.0.
  * `Et::Vector{Float64}`: The vector Et of smoothed deviations from the zero mean. Has to be exactly equal to `zeros(p)`
  * `t::Int`: The current value of time. Default is 0.
  * `stat::C`: The underlying classical MCUSUM statistic. Default is MCUSUM(k=0.1, p=p).

### References

Dai, Y., Luo, Y., Li, Z., & Wang, Z. (2011). A new adaptive CUSUM control chart for detecting the multivariate process mean. Quality and Reliability Engineering International, 27(7), 877-884. https://doi.org/10.1002/qre.1177
