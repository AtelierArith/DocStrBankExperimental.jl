```julia
generalized_a_star_with_threshold(
    instance::ConstrainedShortestPaths.ForwardCSPInstance,
    threshold::Float64;
    kwargs...
) -> @NamedTuple{p_star::Vector{Vector{Int64}}, c_star::Vector{Float64}}

```

Compute all paths below threshold.
