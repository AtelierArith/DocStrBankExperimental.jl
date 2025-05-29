```
init(forward_prob::SimulatorForwardProblem{<:AbstractODEProblem}, ode_alg; p=forward_prob.prob.p, saveat=[], solve_kwargs...)
```

与えられたフォワード問題とODE積分アルゴリズムのために`SimulatorODEForwardSolver`を初期化します。追加のキーワード引数は、積分器の`init`実装に渡されます。
