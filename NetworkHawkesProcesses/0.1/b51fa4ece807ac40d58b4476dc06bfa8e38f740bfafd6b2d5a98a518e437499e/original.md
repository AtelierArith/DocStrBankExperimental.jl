```
rand(p::DiscreteHawkesProcess, steps)
```

Sample a random sequence of events from a discrete Hawkes process.

# Arguments

  * `T::Int64`: the number of time steps to sample.

# Returns

  * `S::Array{Int64,2}`: an `N x T` array of event counts.
