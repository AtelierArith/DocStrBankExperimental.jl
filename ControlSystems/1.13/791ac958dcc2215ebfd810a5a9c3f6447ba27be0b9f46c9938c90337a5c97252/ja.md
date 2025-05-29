```
sol = solve(s::AbstractSimulator, x0, tspan,  args...; kwargs...)
```

初期状態 `x0` から時間範囲 `tspan = (t0,tf)` にわたって `s` で表されるシステムをシミュレートします。 `args` と `kwargs` は `OrdinaryDiffEq` の `solve` 関数に送られます。例えば、`solve(s, x0, tspan,  Tsit5(), reltol=1e-5)` はソルバー [`Tsit5()`](http://docs.juliadiffeq.org/stable/solvers/ode_solve.html) と相対許容誤差 1e-5 で問題を解きます。

`Simulator` `lsim` も参照してください。
