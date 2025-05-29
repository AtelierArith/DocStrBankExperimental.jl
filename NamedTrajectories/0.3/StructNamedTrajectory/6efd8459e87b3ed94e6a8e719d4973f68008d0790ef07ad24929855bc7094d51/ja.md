```
NamedTrajectory(component_data; controls=(), timestep=nothing, bounds, initial, final, goal)

# 引数
- `comps::NamedTuple{names, <:Tuple{Vararg{AbstractMatrix{R}}}} where {names}`: コンポーネントデータ。
- `traj`: 構築された NamedTrajectory。
- `goal`: 状態の目標。
```
