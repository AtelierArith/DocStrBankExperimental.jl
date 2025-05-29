```
struct VariableNotOwned{V <: AbstractVariableRef} <: Exception
    variable::V
end
```

変数 `variable` は `owner_model(variable)` とは異なるモデルで使用されました。
