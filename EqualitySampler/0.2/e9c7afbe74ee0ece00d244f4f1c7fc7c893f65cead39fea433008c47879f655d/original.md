```julia
get_hpm_partition(
    results::EqualitySampler.EnumerateResult
) -> Vector{Int64}

```

Compute the highest posterior probability model/ partition. Note that this can be unstable if the result is not obtained via sampling and the modelspace is very large.
