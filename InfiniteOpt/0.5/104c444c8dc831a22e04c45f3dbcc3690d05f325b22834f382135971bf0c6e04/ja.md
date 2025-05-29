```
JuMP.all_constraints(model::InfiniteModel, [function_type], [set_type])::Vector{InfOptConstraintRef}
```

`JuMP.all_constraints`を拡張して、特定の関数タイプとセットタイプを持つすべての制約のリストを返します。

**例**

```julia-repl
julia> all_constraints(model, GeneralVariableRef, MOI.LessThan)
1-element Array{InfOptConstraintRef,1}:
 x ≤ 1.0

julia> all_constraints(model, GeneralVariableRef)
3-element Array{InfOptConstraintRef,1}:
 x ≥ 0.0
 x ≤ 3.0
 x integer

julia> all_constraints(model, MOI.GreaterThan)
3-element Array{InfOptConstraintRef,1}:
 x ≥ 0.0
 g(t) ≥ 0.0, ∀ t ∈ [0, 6]
 g(0.5) ≥ 0.0

julia> all_constraints(model)
5-element Array{InfOptConstraintRef,1}:
 x ≥ 0.0
 x ≤ 3.0
 x integer
 g(t) ≥ 0.0, ∀ t ∈ [0, 6]
 g(0.5) ≥ 0.0
```
