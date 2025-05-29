```
sim_gbmbd(t   ::Float64;
          λ0  ::Float64 = 1.0,
          μ0  ::Float64 = 0.2,
          α   ::Float64 = 0.0,
          σλ  ::Float64 = 0.1,
          σμ  ::Float64 = 0.1,
          δt  ::Float64 = 1e-3,
          nlim::Int64   = 10_000,
          init::Symbol  = :crown)
```

Simulate `iTbd` according to geometric Brownian motions for birth and death rates.
