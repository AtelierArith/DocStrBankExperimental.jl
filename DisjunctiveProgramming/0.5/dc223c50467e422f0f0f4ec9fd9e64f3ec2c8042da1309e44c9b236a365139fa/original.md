```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::MathOptInterface.Nonpositives,
    tag::Disjunct
)::_DisjunctConstraint
```

Extend `JuMP.build_constraint` to add `VectorConstraint`s to disjuncts.
