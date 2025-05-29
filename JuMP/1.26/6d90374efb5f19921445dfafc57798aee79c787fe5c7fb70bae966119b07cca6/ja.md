```
unset_binary(variable_ref::GenericVariableRef)
```

変数 `variable_ref` のバイナリ制約を削除します。

関連情報としては [`BinaryRef`](@ref)、[`is_binary`](@ref)、[`set_binary`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> is_binary(x)
true

julia> unset_binary(x)

julia> is_binary(x)
false
```
