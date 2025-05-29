```
set_units(var::OutputVar, units::AbstractString)
```

`var`のデータに対して`units`を設定します。

!!! warning "既存の単位を上書きする"
    既に単位が存在する場合、これは`var`のデータの単位を上書きします。単位を変換するには、[`Var.convert_units`](@ref)を参照してください。

