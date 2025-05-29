```
set_gradient!(agst::AbstractGradientSolverState, M, p, X)
```

[`AbstractGradientSolverState`](@ref) 内に保存されている（現在の）勾配を `X` に設定します。デフォルトの関数は `s.X` を変更します。
