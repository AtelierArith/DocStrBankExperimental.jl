```
remake(prob::NonlinearProblem; f = missing, u0 = missing, p = missing,
    problem_type = missing, kwargs = missing, _kwargs...)
```

与えられた `NonlinearProblem` を再構築します。`u0` または `p` がシンボリックマップとして与えられている場合、`ModelingToolkit.jl` をロードする必要があります。
