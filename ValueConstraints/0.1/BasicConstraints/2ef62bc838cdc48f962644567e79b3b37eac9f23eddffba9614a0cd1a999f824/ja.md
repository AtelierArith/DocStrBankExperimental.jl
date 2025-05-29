```julia
struct ExclusiveMaximum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

指定された値より小さい値に制約します。
