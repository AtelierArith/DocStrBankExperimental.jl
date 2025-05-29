`holding_times(markov_chain, number_of_states; dt=1)`

# Description

```
Calculate the holding times of a markov chain.
```

# Arguments

  * `markov_chain::AbstractVector`: A vector of integers representing the state of a markov chain at each time step.
  * `number_of_states::Integer`: The number of states in the markov chain.
  * `dt::Real`: The time step of the markov chain.

# Returns

  * `holding_times::Vector{Vector{Real}}`: A vector of vectors of holding times for each state.
