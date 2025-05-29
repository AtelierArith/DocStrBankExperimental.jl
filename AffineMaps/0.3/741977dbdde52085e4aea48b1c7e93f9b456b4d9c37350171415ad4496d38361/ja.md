```
struct InvMulAdd
```

`f = InvMulAdd(A, b)` は `f(x) == f.A \ (x .- f.b)` の動作を持ちます。これは `MulAdd(A, b)` の逆です。

詳細については [`AbstractAffineMap`](@ref) を参照してください。
