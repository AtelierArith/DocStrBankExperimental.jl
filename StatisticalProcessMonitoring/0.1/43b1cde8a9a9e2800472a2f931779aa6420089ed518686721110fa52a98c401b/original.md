```
TwoSidedBootstrapLimit{T} <: BootstrapLimit{T}
```

A two-sided bootstrap limit with constant false-alarm rate.

# Fields

  * `sim::Vector{T}`: The vector of simulated statistics.
  * `h::Vector{T}`: The current value of the control limits.

# Constructors

  * `TwoSidedBootstrapLimit(S::AbstractStatistic, B::Int)`: Create a new `TwoSidedBootstrapLimit` object. The argument `S` is an `AbstractStatistic` object. The argument `B` is an integer indicating the number of bootstrap replications.
