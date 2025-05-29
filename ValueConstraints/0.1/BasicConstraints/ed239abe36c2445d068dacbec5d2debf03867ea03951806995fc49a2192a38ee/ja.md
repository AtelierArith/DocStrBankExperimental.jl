```julia
struct Not{S<:ValueConstraints.Interface.AbstractConstraint} <: ValueConstraints.Interface.AbstractConstraint
```

  * `constraint::ValueConstraints.Interface.AbstractConstraint`: 反転させる `constraint`。

`constraint` の反転を表します。
