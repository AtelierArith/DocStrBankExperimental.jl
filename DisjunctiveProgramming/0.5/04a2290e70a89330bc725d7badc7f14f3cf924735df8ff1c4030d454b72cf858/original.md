```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::JuMP.Nonnegatives,
    tag::Disjunct
)::_DisjunctConstraint
```

Extend `JuMP.build_constraint` to add `VectorConstraint`s to disjuncts.
