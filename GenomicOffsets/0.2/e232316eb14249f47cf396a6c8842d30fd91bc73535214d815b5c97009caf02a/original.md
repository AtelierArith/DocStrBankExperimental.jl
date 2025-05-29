```
TracyWidom(eigenvalues::AbstractVector{T}; sort_eigenvalues::Bool=true) where T<:Real
```

Compute the Tracy-Widom statistics and p-values for a given set of eigenvalues. TODO: add reference. 

# Arguments

  * `eigenvalues::AbstractVector{T}`: A vector of eigenvalues.
  * `sort_eigenvalues::Bool=true`: If true, sort the eigenvalues in descending order. If false, the eigenvalues are assumed to be sorted in descending order.

# Returns

  * A tuple with the Tracy-Widom statistics and p-values. For a given threshold, it is advised not to keep all eigenvalues below the threshold, but up to the first one that is above the threshold (not included).
