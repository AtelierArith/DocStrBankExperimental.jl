```
sim_gbmpb(n       ::Int64;
          λ0      ::Float64 = 1.0,
          α       ::Float64 = 0.0,
          σλ      ::Float64 = 0.1,
          δt      ::Float64 = 1e-3,
          init    ::Symbol  = :stem,
          nstar   ::Int64   = n + 2,
          p       ::Float64 = 5.0,
          warnings::Bool    = true,
          maxt    ::Float64 = δt*1e7)
```

Simulate `iTpb` according to a pure-birth geometric Brownian motion.
