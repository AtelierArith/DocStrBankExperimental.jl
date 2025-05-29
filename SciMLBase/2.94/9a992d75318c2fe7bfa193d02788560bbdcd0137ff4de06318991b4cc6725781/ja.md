```
remake(prob::OptimizationProblem; f = missing, u0 = missing, p = missing,
    lb = missing, ub = missing, int = missing, lcons = missing, ucons = missing,
    sense = missing, kwargs = missing, _kwargs...)
```

与えられた `OptimizationProblem` を再構築します。`u0` または `p` がシンボリックマップとして与えられている場合、`ModelingToolkit.jl` をロードする必要があります。
