```
unset_integer(variable_ref::GenericVariableRef)
```

変数 `variable_ref` の整数制約を削除します。

存在しない場合はエラーになります。

関連情報としては [`IntegerRef`](@ref)、[`is_integer`](@ref)、[`set_integer`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Int);

julia> is_integer(x)
true

julia> unset_integer(x)

julia> is_integer(x)
false
```
