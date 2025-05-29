```
set_gradient!(s::AbstractManoptSolverState, M::AbstractManifold, p, X)
```

（装飾されている可能性のある）[`AbstractManoptSolverState`](@ref) 内の勾配を、点 `p` における接空間のいくつかの（開始）値 `X` に設定します。
