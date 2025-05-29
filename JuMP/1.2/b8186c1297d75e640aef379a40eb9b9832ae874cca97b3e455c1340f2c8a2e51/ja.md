```
is_fixed(v::VariableRef)
```

`v`が固定変数である場合は`true`を返します。`true`の場合、固定値は[`fix_value`](@ref)で照会できます。

関連情報として、[`FixRef`](@ref)、[`fix_value`](@ref)、[`fix`](@ref)、[`unfix`](@ref)を参照してください。
