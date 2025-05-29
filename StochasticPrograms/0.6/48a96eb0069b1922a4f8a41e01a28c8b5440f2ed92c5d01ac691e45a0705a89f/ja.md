```
value(dvar_expr::Union{GenericAffExpr{T,DecisionVariable}, GenericQuadExpr{T,DecisionVariable}}, stage_to_scenario::Dict{Int,Int}) where T
```

与えられた `stage_to_scenario` マップによって返されるシナリオで `dvar` の値が見つかる場合に `dvar_expr` を評価します。
