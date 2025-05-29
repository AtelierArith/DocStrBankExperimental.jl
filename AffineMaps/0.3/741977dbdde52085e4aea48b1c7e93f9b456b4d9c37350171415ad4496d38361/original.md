```
struct InvMulAdd
```

`f = InvMulAdd(A, b)` has the behavior `f(x) == f.A \ (x .- f.b)`. It is the inverse of `MulAdd(A, b)`.

See [`AbstractAffineMap`](@ref) for more information.
