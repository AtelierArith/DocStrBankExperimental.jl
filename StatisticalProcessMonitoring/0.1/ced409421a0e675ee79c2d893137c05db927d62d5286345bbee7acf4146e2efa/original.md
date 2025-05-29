```
TRAS{F,D}
```

# Fields

A Top-r-based Adaptive Sampling monitoring statistic for monitoring multiple data streams with partial observations.

## Fields

  * `k::Float64`: The allowance constant for the CUSUM statistic. Defaults to `0.1`.
  * `mu_min::Float64`: The minimum shift to be detected. Defaults to `1.0`.
  * `value::Float64`: The current value of the monitoring statistic. Defaults to `0.0`.
  * `Δ::Float64`: The compensation coefficient for non-observed variables.
  * `r::Int`: The number of largest variables to sum.
  * `q::Int`: The total number of observable variables.
  * `p::Int`: The total number of variables.
  * `W::Vector{Float64}`: The vector of local monitoring statistics. Defaults to a vector of zeros.
  * `W1::Vector{Float64}`: The vector used to store the local monitoring statistics to detect increases in the mean. Defaults to a vector of zeros.
  * `W2::Vector{Float64}`: The vector used to store the local monitoring statistics to detect decreases in the mean. Defaults to a vector of zeros.
  * `obs::Vector{Int}`: The selected indices of the top `q` values of local monitoring statistics. Defaults to a random sample of size `q` from the range `1:p`.
  * `sampler::S`: The sampling strategy used to select the next set of `obs` indices. Defaults to `ThompsonSampling()`.

# References

Liu, K., Mei, Y., & Shi, J. (2015). An Adaptive Sampling Strategy for Online High-Dimensional Process Monitoring. Technometrics, 57(3), 305-319. https://doi.org/10.1080/00401706.2014.947005
