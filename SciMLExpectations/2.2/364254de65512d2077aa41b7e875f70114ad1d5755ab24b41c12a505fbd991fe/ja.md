```julia
solve(exprob::ExpectationProblem, expalg::Koopman;
      maxiters = 1000000, batch = nothing, quadalg = HCubatureJL(),
      ireltol = 1e-2, iabstol = 1e-2, kwargs...)
```

`ExpectationProblem`をKoopman積分を使用して解きます。
