```julia
sample_names(state, log_potential, extractor)

```

A list of string labels for the flattened vectors returned by [`extract_sample()`](@ref).

The key `:log_density` is used when the un-normalized log density  is included.
