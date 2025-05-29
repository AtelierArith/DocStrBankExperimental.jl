```julia
struct Is{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

値を特定の値に制約します。
