```
value(dvar_expr::Union{GenericAffExpr{T,DecisionVariable}, GenericQuadExpr{T,DecisionVariable}}, stage_to_scenario::Dict{Int,Int}) where T
```

Evaluate `dvar_expr` where the value of a given `dvar` is found in the scenario returned by the provided `stage_to_scenario` map.
