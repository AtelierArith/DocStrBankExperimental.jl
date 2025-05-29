```
SSRootfind(alg = nothing)
```

非線形ソルバーを使用して定常状態を見つけます。最初の引数として非線形ソルバーが必要です。

!!! note
    デフォルトの `alg` の `nothing` は、`NonlinearSolve.jl` がインストールされて読み込まれている場合にのみ機能します。

