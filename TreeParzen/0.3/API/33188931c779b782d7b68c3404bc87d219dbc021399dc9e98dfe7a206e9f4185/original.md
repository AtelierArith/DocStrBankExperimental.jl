```julia
ask(
    space::Union{TreeParzen.Types.AbstractDelayed, Dict{Symbol}, AbstractVector},
    trials::Vector{TreeParzen.Trials.Trial},
    config::TreeParzen.Configuration.Config
) -> TreeParzen.Trials.Trial

```

Provides a suggestion based on tree-parzen estimation
