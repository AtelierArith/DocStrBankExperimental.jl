```
intensity(process::ContinuousHawkesProcess, data, times)
```

Calculate the intensity of `process` at `times` given `data`.

# Arguments

  * `data::Tuple{Vector{Float64},Vector{Int64},Float64}`: a tuple containing a vector of events, a vector of nodes associated with each event, and the duration of the data sample.
  * `times::Vector{Float64}`: a vector times where the process intensity will be computed.

# Returns

  * `λ::Vector{Float64}`: a `len(times)` array of intensities conditional on `data` and `process`.
