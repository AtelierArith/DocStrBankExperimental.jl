```
is_binary(v::GenericVariableRef)
```

`v`がバイナリに制約されている場合は`true`を返します。

関連情報としては、[`BinaryRef`](@ref)、[`set_binary`](@ref)、[`unset_binary`](@ref)があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> is_binary(x)
true
```
