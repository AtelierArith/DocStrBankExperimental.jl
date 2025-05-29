```julia
struct Maximum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: 検証するための `value`。

指定された値以下であることを値に制約します。
