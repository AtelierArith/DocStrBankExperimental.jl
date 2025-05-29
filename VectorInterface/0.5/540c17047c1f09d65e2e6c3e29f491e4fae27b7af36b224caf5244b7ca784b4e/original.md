```
scale!(x, α::Number) -> x
scale!(y, x, α::Number) -> y
```

Rescale `x` with the scalar coefficient `α`, thereby overwrite and thus recylcing the contents of `x` (in the first form) or `y` (in the second form). This is only possible if `x`, respectively `y` is mutable, and if the scalar types involed are compatible and can be promoted and converted.

Also see: [`scale`](@ref) and [`scale!!`](@ref)
