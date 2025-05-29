```
set_iterate!(agst::AbstractGradientSolverState, M, p)
```

[`AbstractGradientSolverState`](@ref) 内に保存されている（現在の）反復値を `p` に設定します。デフォルトの関数は `s.p` を変更します。
