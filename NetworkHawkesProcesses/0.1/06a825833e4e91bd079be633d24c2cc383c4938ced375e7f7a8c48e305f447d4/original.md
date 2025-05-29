```
rand(process::ContinuousHawkesProcess, duration)
```

Sample a random sequence of events from a continuous Hawkes process.

# Arguments

  * `duration::Float64`: the sample duration.

# Returns

  * `data::Tuple{Vector{Float64},Vector{Int64},Float64}`: a tuple containing a vector of events, a vector of nodes associated with each event, and the duration of the data sample.
