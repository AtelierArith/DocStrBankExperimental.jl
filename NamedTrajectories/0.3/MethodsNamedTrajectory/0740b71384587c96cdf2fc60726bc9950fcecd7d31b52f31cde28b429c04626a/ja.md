```
update_bound!(traj, name::Symbol, data::Real)
update_bound!(traj, name::Symbol, data::AbstractVector{<:Real})
update_bound!(traj, name::Symbol, data::Tuple{R, R} where R <: Real)
```

軌道のコンポーネントの境界を更新します。
