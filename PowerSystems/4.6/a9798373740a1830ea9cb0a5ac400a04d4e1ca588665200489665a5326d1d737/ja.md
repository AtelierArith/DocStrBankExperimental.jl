```julia
set_angle_limits!(
    value::PowerSystems.DynamicBranch,
    val::@NamedTuple{min::Float64, max::Float64}
) -> @NamedTuple{min::Float64, max::Float64}

```

DynamicBranchのangle_limitsを設定します。
