```
set_integer(variable_ref::GenericVariableRef)
```

変数 `variable_ref` に整数制約を追加します。

関連情報としては [`IntegerRef`](@ref), [`is_integer`](@ref), [`unset_integer`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_integer(x)
false

julia> set_integer(x)

julia> is_integer(x)
true
```
