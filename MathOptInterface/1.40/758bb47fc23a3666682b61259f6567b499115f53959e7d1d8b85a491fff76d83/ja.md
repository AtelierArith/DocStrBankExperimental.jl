```
constant(set::Union{EqualTo,GreaterThan,LessThan,Parameter})
```

セット `set` の定数項を返します。

## 例

```jldoctest
julia> MOI.constant(MOI.GreaterThan(1.0))
1.0

julia> MOI.constant(MOI.LessThan(2.5))
2.5

julia> MOI.constant(MOI.EqualTo(3))
3

julia> MOI.constant(MOI.Parameter(4.5))
4.5
```
