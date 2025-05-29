```
function JuMP.add_constraint(
    model::JuMP.GenericModel,
    c::JuMP.ScalarConstraint{_LogicalExpr, MOI.EqualTo{Bool}},
    name::String = ""
)
```

`JuMP.add_constraint`を拡張して、`@constraint`マクロを使用して[`GDPModel`](@ref)の論理命題制約を作成できるようにします。ユーザーは、`@constraint(model, logical_expr := true)`という構文を使用して論理制約を定義する必要があります。
