```
sim_gbmbd(n       ::Int64;
          λ0      ::Float64 = 1.0,
          μ0      ::Float64 = 0.1,
          α       ::Float64 = 0.0,
          σλ      ::Float64 = 0.1,
          σμ      ::Float64 = 0.1,
          init    ::Symbol  = :stem,
          δt      ::Float64 = 1e-3,
          nstar   ::Int64   = 2*n,
          p       ::Float64 = 5.0,
          warnings::Bool    = true)
```

Simulate `iTbd` according to geometric Brownian motions for birth and death rates.
