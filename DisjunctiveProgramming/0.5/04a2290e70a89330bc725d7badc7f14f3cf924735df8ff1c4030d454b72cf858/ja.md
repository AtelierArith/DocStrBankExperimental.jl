```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::JuMP.Nonnegatives,
    tag::Disjunct
)::_DisjunctConstraint
```

`JuMP.build_constraint`を拡張して、disjunctsに`VectorConstraint`を追加します。
