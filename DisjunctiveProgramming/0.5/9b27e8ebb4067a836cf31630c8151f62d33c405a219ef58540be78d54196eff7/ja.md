```
requires_variable_bound_info(method::AbstractReformulationMethod)::Bool
```

`method` が [`variable_bound_info`](@ref) を介してアクセスされる変数の境界情報を必要とするかどうかを示す `Bool` を返します。必要に応じて新しい [`AbstractReformulationMethod`](@ref) メソッドに対してこれを拡張する必要があります（デフォルトは `false` です）。新しいメソッドが変数の境界情報を必要とする場合は、[`set_variable_bound_info`](@ref) も拡張する必要があります。
