```
sim_gbmpb(t   ::Float64;
          λ0  ::Float64 = 1.0,
          α   ::Float64 = 0.0,
          σλ  ::Float64 = 0.1,
          δt  ::Float64 = 1e-3,
          nlim::Int64   = 10_000,
          init::Symbol  = :crown)
```

Simulate `iTpb` according to a pure-birth geometric Brownian motion conditional in stopping at time `t`.
