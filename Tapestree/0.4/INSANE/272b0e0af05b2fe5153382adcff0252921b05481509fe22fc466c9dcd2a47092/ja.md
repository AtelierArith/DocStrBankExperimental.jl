```
sim_gbmct(t   ::Float64;
          λ0  ::Float64 = 1.0,
          α   ::Float64 = 0.0,
          σλ  ::Float64 = 0.1,
          ϵ   ::Float64 = 0.2,
          δt  ::Float64 = 1e-3,
          nlim::Int64   = 10_000,
          init::Symbol  = :crown)
```

出生率と一定の回転率に従って幾何ブラウン運動に基づいて `iTct` をシミュレートします。
