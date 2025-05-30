```
GlobalEqualityConstraint(
    name::Symbol,
    val::Vector{Float64},
    traj::NamedTrajectory;
    label="グローバル変数[name]に対する等式制約"
)::EqualityConstraint
```

グローバル変数に対する等式制約をNamedTrajectoryで構築します。
