```julia
get_dP_lim(
    value::PowerSystems.ActiveRenewableControllerAB
) -> @NamedTuple{min::Float64, max::Float64}

```

[`ActiveRenewableControllerAB`](@ref) の `dP_lim` を取得します。
