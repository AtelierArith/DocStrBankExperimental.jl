```
GlobalEqualityConstraint(
    name::Symbol,
    val::Vector{Float64},
    traj::NamedTrajectory;
    label="グローバル変数[name]に対する等式制約"
)::EqualityConstraint
```

NamedTrajectory内のグローバル変数に対する等式制約を構築します。
