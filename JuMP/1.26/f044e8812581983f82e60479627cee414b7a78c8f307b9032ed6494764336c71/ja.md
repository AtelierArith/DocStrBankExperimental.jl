```
lower_bound(v::GenericVariableRef)
```

変数の下限を返します。存在しない場合はエラーになります。

関連情報としては [`LowerBoundRef`](@ref)、[`has_lower_bound`](@ref)、[`set_lower_bound`](@ref)、[`delete_lower_bound`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> lower_bound(x)
1.0
```
