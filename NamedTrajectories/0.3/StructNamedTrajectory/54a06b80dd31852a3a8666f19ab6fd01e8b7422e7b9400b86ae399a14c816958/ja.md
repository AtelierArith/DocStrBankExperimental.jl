```
NamedTrajectory(component_data; controls=(), timestep=nothing, bounds, initial, final, goal)

# 引数
- `component_data::NamedTuple{names, <:Tuple{Vararg{AbstractMatrix{R}}}} where {names}`: コンポーネントデータ。
- `controls`: component_data内の制御変数で、`Symbol`型である必要があります。
- `timestep`: component_data内の離散化時間ステップで、`Symbol`型である必要があります。
- `bounds`: 軌道の境界。
- `initial`: 初期値。
- `final`: 最終値。
- `goal`: 状態の目標。
```
