```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::_MOI.AbstractScalarSet,
    tag::Disjunct
)::_DisjunctConstraint
```

Extend `JuMP.build_constraint` to add constraints to disjuncts. This in  combination with `JuMP.add_constraint` enables the use of  `@constraint(model, [name], constr_expr, tag)`, where tag is a `Disjunct(::Type{LogicalVariableRef})`. The user must specify the  `LogicalVariable` to use as the indicator for the `_DisjunctConstraint` being created.
