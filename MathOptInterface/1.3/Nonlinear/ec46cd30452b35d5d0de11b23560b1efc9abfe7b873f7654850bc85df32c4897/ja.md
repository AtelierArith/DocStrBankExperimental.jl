```
ConstraintIndex
```

非線形制約に対するインデックスで、[`add_constraint`](@ref)によって返されます。

`data::Model`と`c::ConstraintIndex`が与えられた場合、`data[c]`を使用して対応する[`Constraint`](@ref)を取得します。
