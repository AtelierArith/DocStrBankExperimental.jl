```
sim_gbmct(n       ::Int64;
          λ0      ::Float64 = 1.0,
          α       ::Float64 = 0.0,
          σλ      ::Float64 = 0.1,
          ϵ       ::Float64 = 0.0,
          δt      ::Float64 = 1e-3,
          init    ::Symbol  = :stem,
          nstar   ::Int64   = 2*n,
          p       ::Float64 = 5.0,
          warnings::Bool    = true,
          maxt    ::Float64 = δt*1e7)
```

Simulate `iTct` according to a geometric Brownian motion for birth rates and constant turnover.
