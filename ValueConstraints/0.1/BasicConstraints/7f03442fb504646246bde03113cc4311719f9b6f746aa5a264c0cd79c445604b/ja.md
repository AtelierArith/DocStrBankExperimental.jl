```julia
struct ExclusiveMinimum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

指定された値より大きい値に制限します。
