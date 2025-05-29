```julia
get_states_types(
    d::PowerSystems.DynamicComponent
) -> Vector{PowerSystems.StateTypesModule.StateTypes}

```

```
動的コンポーネントのためのget_state_typesのデフォルト実装。すべての状態が
微分であると仮定します。
```
