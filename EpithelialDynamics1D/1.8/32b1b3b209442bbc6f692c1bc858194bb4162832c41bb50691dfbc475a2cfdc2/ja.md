```
SteadyCellProblem{M}
```

[`CellProblem`](@ref) の定常状態問題を定義します。単一のフィールド `prob::CellProblem` のみを持ちます。

この問題は、`NonlinearProblem` と同様に `solve` することができます。例えば、

```
solve(prob, alg)
```

ここで `alg` は、SteadyStateDiffEq.jl からの `DynamicSS(TRBDF2())` などです。
