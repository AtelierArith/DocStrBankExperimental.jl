```julia
struct MultipleOf{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

指定された値の倍数であることを制約します。
