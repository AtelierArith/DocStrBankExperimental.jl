```
intensity(process::DiscreteHawkesProcess, convolved)
```

Calculate the intensity at time all times `t ∈ [1, 2, ..., T]` given pre-convolved event data.

# Arguments

  * `convolved::Array{Float64,3}`: `T x N x B` array of event counts convolved with basis functions.

# Returns

  * `λ::Array{Float64,2}`: a `T x N` array of intensities conditional on the convolved event counts.
