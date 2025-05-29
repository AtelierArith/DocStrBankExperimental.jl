```
replicator_dynamics!(dx::Vector{Float64}, x::Vector{Float64}, params::ReplicatorParams, t::Float64)
```

Computes the time derivative of the replicator dynamics for a population playing three strategies.

# Arguments

  * `dx`: A vector to store the time derivative (change in frequencies).
  * `x`: A vector representing the current frequencies of the three strategies.
  * `params`: A `ReplicatorParams` struct containing the payoff functions and extra parameters.
  * `t`: The current time in the dynamics.

# Notes

  * The function normalizes `x` to ensure the frequencies sum to 1 before computing the payoffs.
  * The replicator dynamics equation is: `dxᵢ = xᵢ * (wᵢ - w̄)`, where `wᵢ` is the payoff of strategy `i` and `w̄` is the average payoff.
