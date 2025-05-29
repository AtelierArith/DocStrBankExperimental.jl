```julia
struct IsA{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

特定の型であることを値に制約します。
