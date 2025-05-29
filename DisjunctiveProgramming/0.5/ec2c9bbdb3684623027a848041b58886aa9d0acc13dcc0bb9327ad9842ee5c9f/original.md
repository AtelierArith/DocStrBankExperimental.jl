```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::JuMP.Zeros,
    tag::Disjunct
)::_DisjunctConstraint
```

Extend `JuMP.build_constraint` to add `VectorConstraint`s to disjuncts.
