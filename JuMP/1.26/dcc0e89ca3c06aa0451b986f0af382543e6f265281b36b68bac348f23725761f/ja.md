```
has_upper_bound(v::GenericVariableRef)
```

`v`に上限がある場合は`true`を返します。`true`の場合、上限は[`upper_bound`](@ref)で照会できます。

また、[`UpperBoundRef`](@ref)、[`upper_bound`](@ref)、[`set_upper_bound`](@ref)、[`delete_upper_bound`](@ref)も参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> has_upper_bound(x)
true
```
