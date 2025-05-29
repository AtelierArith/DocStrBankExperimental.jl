```
IntegerRef(v::GenericVariableRef)
```

`v`を整数に制約する制約の参照を返します。

存在しない場合はエラーになります。

関連情報としては、[`is_integer`](@ref)、[`set_integer`](@ref)、[`unset_integer`](@ref)があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Int);

julia> IntegerRef(x)
x integer
```
