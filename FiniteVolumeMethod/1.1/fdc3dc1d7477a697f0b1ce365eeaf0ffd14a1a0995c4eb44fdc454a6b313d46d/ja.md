```
solve(prob::AbstractFVMTemplate, args...; kwargs...)
```

問題 `prob` を DifferentialEquations.jl の標準 `solve` インターフェースを使用して解きます。定常状態の問題については、インターフェースは LinearSolve.jl からのものです。
