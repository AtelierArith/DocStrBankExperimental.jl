```
EqualityConstraint(
    name::Symbol,
    ts::Vector{Int},
    val::Vector{Float64},
    traj::NamedTrajectory;
    label="equality constraint on trajectory variable [name]"
)
```

NamedTrajectoryの軌道変数に対する等式制約を構築します。
