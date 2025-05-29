```julia
get_mpm_partition(eq_probs::AbstractMatrix) -> Any
get_mpm_partition(
    eq_probs::AbstractMatrix,
    threshhold
) -> Any

```

Compute the median posterior probability model/ partition. Note that this is not the same as the median model/ partition in regression. For partitions, we find the partition `p` that minimizes `sum(abs2(eq_probs[i, j] - (p[i] == p[j])) for i in eachindex(p), j in eachindex(p))`. This is done in a heuristic manner, so the result is not guaranteed to be the true mpm.
