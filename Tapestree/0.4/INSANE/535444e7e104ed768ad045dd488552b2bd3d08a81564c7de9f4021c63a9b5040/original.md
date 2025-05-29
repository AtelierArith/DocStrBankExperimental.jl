```
sim_gbmce(t   ::Float64;
          λ0  ::Float64 = 1.0,
          α   ::Float64 = 0.0,
          σλ  ::Float64 = 0.1,
          μ   ::Float64 = 0.2,
          δt  ::Float64 = 1e-3,
          nlim::Int64   = 10_000,
          init::Symbol  = :crown)
```

Simulate `iTce` according to a geometric Brownian motion for birth rates and constant extinction.
