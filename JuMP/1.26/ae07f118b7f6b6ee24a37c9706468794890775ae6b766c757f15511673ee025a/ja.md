```
LowerBoundRef(v::GenericVariableRef)
```

`v`の下限制約への参照を返します。

存在しない場合はエラーになります。

他にも[`has_lower_bound`](@ref)、[`lower_bound`](@ref)、[`set_lower_bound`](@ref)、[`delete_lower_bound`](@ref)を参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> LowerBoundRef(x)
x ≥ 1
```
