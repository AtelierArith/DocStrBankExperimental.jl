```
has_lower_bound(v::GenericVariableRef)
```

`v` に下限がある場合は `true` を返します。`true` の場合、下限は [`lower_bound`](@ref) で照会できます。

他に [`LowerBoundRef`](@ref)、[`lower_bound`](@ref)、[`set_lower_bound`](@ref)、[`delete_lower_bound`](@ref) も参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> has_lower_bound(x)
true
```
