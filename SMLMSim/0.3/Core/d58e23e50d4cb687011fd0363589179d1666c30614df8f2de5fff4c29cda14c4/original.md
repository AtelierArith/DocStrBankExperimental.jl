```
CTMC(q::Array{T}, simulation_time::T, state1::Int) where {T<:AbstractFloat}
```

Construct a Continuous Time Markov Chain simulation from a rate matrix.

# Arguments

  * `q::Array{T}`: Rate matrix where q[i,j] for i≠j is the transition rate from state i to j, and q[i,i] is the negative exit rate from state i
  * `simulation_time::T`: Total time to simulate
  * `state1::Int`: Initial state

# Returns

  * `CTMC{T,Int}`: Simulated CTMC with transition times and states

# Details

Simulates a CTMC using the Gillespie algorithm:

1. Start in state1 at time 0
2. For current state i:

      * Calculate total exit rate k*tot = Σ*j q[i,j]
      * Sample time until next transition from Exp(k_tot)
      * Sample next state j with probability q[i,j]/k_tot
3. Repeat until exceeding simulation_time
