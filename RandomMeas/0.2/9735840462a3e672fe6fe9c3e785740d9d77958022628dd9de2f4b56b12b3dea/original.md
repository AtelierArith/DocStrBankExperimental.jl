```
apply_depo_channel(ψ::MPS, p::Vector{Float64})
```

Apply the local depolarization channel to an MPS by converting it to an MPO density matrix (using the outer product) and then applying the depolarization channel.

# Arguments

  * `ψ::MPS`: The input Matrix Product State representing a pure state.
  * `p::Vector{Float64}`: A vector of depolarization probabilities, one per site.

# Returns

An MPO representing the depolarized density matrix.
