```
upper_bound(v::GenericVariableRef)
```

変数の上限を返します。

存在しない場合はエラーになります。

関連情報としては [`UpperBoundRef`](@ref)、[`has_upper_bound`](@ref)、[`set_upper_bound`](@ref)、[`delete_upper_bound`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> upper_bound(x)
1.0
```
