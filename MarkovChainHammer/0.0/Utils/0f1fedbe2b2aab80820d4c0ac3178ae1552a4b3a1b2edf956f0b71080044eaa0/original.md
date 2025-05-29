```
autocovariance(g⃗, Ps::Vector{Matrix{Float64}}, steps::Int; progress = false)
```

Calculate the autocovariance of observable g⃗ with transition matrices Ps and number of steps.

# Arguments

  * `g⃗::AbstractVector`: observable
  * `Ps::Vector{Matrix{Float64}}`: transition matrices
  * `steps::Int`: number of steps

# Keyword Arguments

  * `progress::Bool=false`: show a progress bar

# Returns

  * `autocov::Vector`: autocovariance of observable g⃗ with transition matrices Ps and number of steps
