```
reformulate_disjunction(
    model::JuMP.AbstractModel, 
    disj::Disjunction,
    method::AbstractReformulationMethod
) where {T<:Disjunction}
```

指定された`method`を使用して論理和を再定式化します。現在の再定式化方法には`BigM`、`Hull`、および`Indicator`が含まれます。このメソッドは他の再定式化技術に対して拡張可能です。

`disj`フィールドは、`GDPData`オブジェクトの`disjunctions`フィールドに格納されている論理和の`ConstraintData`オブジェクトです。
