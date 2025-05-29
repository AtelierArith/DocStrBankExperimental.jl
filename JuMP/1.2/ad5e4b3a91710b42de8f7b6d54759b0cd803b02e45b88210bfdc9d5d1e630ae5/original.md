```
struct VariableNotOwned{V <: AbstractVariableRef} <: Exception
    variable::V
end
```

The variable `variable` was used in a model different to `owner_model(variable)`.
