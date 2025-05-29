```
JuMP.num_constraints(model::InfiniteModel, [function_type], [set_type])::Int
```

`JuMP.num_constraints`を拡張して、特定の関数タイプとセットタイプを持つ制約の数を返します。

**例**

```julia-repl
julia> num_constraints(model, FiniteVariableRef, MOI.LessThan)
1

julia> num_constraints(model, FiniteVariableRef)
3

julia> num_constraints(model, MOI.LessThan)
2

julia> num_constraints(model)
4
```
