```
BatchDuplicatedNoNeed(x, ∂f_∂xs)
```

[`DuplicatedNoNeed`](@ref)と同様ですが、すべての導関数を一度に計算するための複数のシャドウを含みます。引数`∂f_∂xs`は、型`x`のいくつかの値のタプルである必要があります。
