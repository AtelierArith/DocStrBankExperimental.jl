```
get_optimizer_attribute(model, name::String)
```

`name`という名前のソルバー固有の属性に関連付けられた値を返します。

これは、`get_optimizer_attribute(model, MOI.RawOptimizerAttribute(name))`と同等であることに注意してください。

## 例

```julia
get_optimizer_attribute(model, "SolverSpecificAttributeName")
```

参照: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref).
