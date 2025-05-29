```
current_state(ds::DynamicalSystem) → u::AbstractArray
```

`ds`の現在の状態を返します。この状態は`ds`が変更されると変更されます。参照してください [`initial_state`](@ref), [`observe_state`](@ref).
