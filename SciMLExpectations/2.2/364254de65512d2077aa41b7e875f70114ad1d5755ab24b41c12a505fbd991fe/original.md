```julia
solve(exprob::ExpectationProblem, expalg::Koopman;
      maxiters = 1000000, batch = nothing, quadalg = HCubatureJL(),
      ireltol = 1e-2, iabstol = 1e-2, kwargs...)
```

Solve an `ExpectationProblem` using Koopman integration.
