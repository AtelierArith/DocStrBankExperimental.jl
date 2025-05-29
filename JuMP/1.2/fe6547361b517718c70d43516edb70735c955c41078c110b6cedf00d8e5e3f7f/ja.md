```
get_optimizer_attribute(
    model::Model, attr::MOI.AbstractOptimizerAttribute
)
```

モデル内のソルバー固有の属性 `attr` の値を返します。

## 例

```julia
get_optimizer_attribute(model, MOI.Silent())
```

関連情報: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref).
