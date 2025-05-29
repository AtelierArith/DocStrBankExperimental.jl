```
UpperBoundRef(v::GenericVariableRef)
```

`v`の上限制約への参照を返します。

存在しない場合はエラーになります。

他にも[`has_upper_bound`](@ref)、[`upper_bound`](@ref)、[`set_upper_bound`](@ref)、[`delete_upper_bound`](@ref)を参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> UpperBoundRef(x)
x ≤ 1
```
