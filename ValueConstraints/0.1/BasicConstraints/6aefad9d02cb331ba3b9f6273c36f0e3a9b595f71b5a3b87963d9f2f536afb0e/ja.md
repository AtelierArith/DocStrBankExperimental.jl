```julia
struct Never <: ValueConstraints.Interface.AbstractConstraint
```

どんな`value`がそれに対して検証されても*無効*な制約を表します。
