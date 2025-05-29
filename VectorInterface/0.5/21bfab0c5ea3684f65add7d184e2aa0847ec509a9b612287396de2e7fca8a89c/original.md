```
scale!!(x, α::Number)
scale!!(y, x, α::Number)
```

Rescale `x` with the scalar coefficient `α`, thereby trying to overwrite and thus recylce the contents of `x` (in the first form) or `y` (in the second form).  A new object will be created when this fails due to immutability, incompatible scalar types or incommensurate sizes.

Also see: [`scale`](@ref) and [`scale!`](@ref)
