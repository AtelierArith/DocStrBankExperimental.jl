```
BinaryRef(v::GenericVariableRef)
```

`v`をバイナリに制約する制約の参照を返します。存在しない場合はエラーになります。

関連情報としては、[`is_binary`](@ref)、[`set_binary`](@ref)、[`unset_binary`](@ref)があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> BinaryRef(x)
x binary
```
