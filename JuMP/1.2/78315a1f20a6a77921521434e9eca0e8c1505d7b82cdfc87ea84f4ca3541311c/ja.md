```
set_optimizer_attribute(
    model::Model,
    attr::MOI.AbstractOptimizerAttribute,
    value,
)
```

モデル内のソルバー固有の属性 `attr` を `value` に設定します。

## 例

```julia
set_optimizer_attribute(model, MOI.Silent(), true)
```

関連項目: [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).
