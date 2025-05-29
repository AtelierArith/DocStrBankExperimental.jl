```
NormalFormGame(payoffs)
```

Construct an N-player NormalFormGame for N>=2 with an array `payoffs` of M=N+1 dimensions, where `payoffs[a_1, a_2, ..., a_N, :]` contains a profile of N payoff values.

# Arguments

  * `payoffs::Array{T<:Real}` : Array with ndims=N+1 containing payoff profiles.
