```
loglikelihood(process::DiscreteHawkesProcess, data)
loglikelihood(process::DiscreteHawkesProcess, data, convolved)
```

Calculate the log-likelihood of `data`. Providing `convolved` skips computation of the convolution step.

# Arguments

  * `data::Array{Int64,2}`: `N x T` array of event counts.
  * `convolved::Array{Float64,3}`: `T x N x B` array of event counts convolved with basis functions.

# Returns

  * `ll::Float64`: the log-likelihood of the event counts.
