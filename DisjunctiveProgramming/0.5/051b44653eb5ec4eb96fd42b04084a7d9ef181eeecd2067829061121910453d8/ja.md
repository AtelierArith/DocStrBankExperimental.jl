```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::_MOI.AbstractScalarSet,
    tag::Disjunct
)::_DisjunctConstraint
```

`JuMP.build_constraint`を拡張して、分離条件に制約を追加します。これにより、`JuMP.add_constraint`と組み合わせて、`@constraint(model, [name], constr_expr, tag)`を使用できるようになります。ここで、tagは`Disjunct(::Type{LogicalVariableRef})`です。ユーザーは、作成される`_DisjunctConstraint`のインジケーターとして使用する`LogicalVariable`を指定する必要があります。
