```
SteadyMBProblem{M}
```

Defines a steady-state problem for a moving boundary problem. Only has a  single field, `prob::MBProblem`.

You can `solve` this problem as you would a `NonlinearProblem`, e.g. with 

```
solve(prob, alg)
```

where `alg` is e.g. `DynamicSS(TRBDF2()))` from SteadyStateDiffEq.jl.
