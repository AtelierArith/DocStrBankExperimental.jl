```
JuMP.build_constraint(
    _error::Function, 
    func, 
    set::MathOptInterface.Zeros,
    tag::Disjunct
)::_DisjunctConstraint
```

`JuMP.build_constraint`を拡張して、ディスジャンクトに`VectorConstraint`を追加します。
