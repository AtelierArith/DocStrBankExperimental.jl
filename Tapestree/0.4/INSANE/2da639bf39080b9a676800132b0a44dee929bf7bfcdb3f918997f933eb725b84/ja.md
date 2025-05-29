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

出生率と死亡率のための幾何ブラウン運動に従って `iTbd` をシミュレートします。
