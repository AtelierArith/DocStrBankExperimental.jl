```
loglikelihood(process::ContinuousHawkesProcess, data)
```

Calculate the log-likelihood of `data`.

# Arguments

  * `data::Tuple{Vector{Float64},Vector{Int64},Float64}`: a tuple containing a vector of events, a vector of nodes associated with each event, and the duration of the data sample.
  * `recursive::Bool`: use recursive formulation, if possible.

# Returns

  * `ll::Float64`: the log-likelihood of the data.
