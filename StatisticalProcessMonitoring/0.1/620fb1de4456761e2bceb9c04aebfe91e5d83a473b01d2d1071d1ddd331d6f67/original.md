```
OneSidedBootstrapLimit{T} <: BootstrapLimit{T}
```

A one-sided bootstrap limit with constant false-alarm rate.

# Fields

  * `sim::Vector{T}`: The vector of simulated statistics.
  * `h::T`: The current value of the control limit.
  * `upw::Bool`: Whether the control limit is an upper or lower control limit.

# Constructors

  * `OneSidedBootstrapLimit(S::AbstractStatistic, upw, B::Int)`: Create a new `OneSidedBootstrapLimit` object. The argument `S` is an `AbstractStatistic` object. The argument `upw` determines whether the bootstrap is one-sided and upper-tailed or lower-tailed. The argument `B` is an integer indicating the number of bootstrap replications.
