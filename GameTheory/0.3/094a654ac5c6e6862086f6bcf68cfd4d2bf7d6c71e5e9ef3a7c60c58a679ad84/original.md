```
NormalFormGame(payoffs)
```

Construct an N-player NormalFormGame with an N-dimensional array `payoffs` of vectors, where `payoffs[a_1, a_2, ..., a_N]` contains a vector of N payoff values, one for each player, for the action profile (a_1, a_2, ..., a_N).

# Arguments

  * `payoffs::Array{AbstractVector{T<:Real}}` : Array with ndims=N containing payoff profiles as vectors.
