```
replace_const_shapes(f::Function, shape::AbstractValueShape)
```

If `shape` is a, or contains, [`ConstValueShape`](@ref) shape(s), recursively replace it/them with the result of `f(s::Shape)`.
