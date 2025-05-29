```julia
struct Minimum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

指定された値以上であることを値に制約します。
