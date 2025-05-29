```
replace_const_shapes(f::Function, shape::AbstractValueShape)
```

もし `shape` が [`ConstValueShape`](@ref) 形状であるか、またはそれを含む場合、再帰的にそれを `f(s::Shape)` の結果で置き換えます。
