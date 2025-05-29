```
set_optimizer_attribute(model::Model, name::String, value)
```

`name`で識別されるソルバー固有の属性を`value`に設定します。

これは、`set_optimizer_attribute(model, MOI.RawOptimizerAttribute(name), value)`と同等であることに注意してください。

## 例

```julia
set_optimizer_attribute(model, "SolverSpecificAttributeName", true)
```

関連情報: [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).
