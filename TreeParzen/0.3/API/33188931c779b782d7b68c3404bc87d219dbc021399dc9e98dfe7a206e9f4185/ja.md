```julia
ask(
    space::Union{TreeParzen.Types.AbstractDelayed, Dict{Symbol}, AbstractVector},
    trials::Vector{TreeParzen.Trials.Trial},
    config::TreeParzen.Configuration.Config
) -> TreeParzen.Trials.Trial

```

ツリーパルゼン推定に基づいて提案を提供します
