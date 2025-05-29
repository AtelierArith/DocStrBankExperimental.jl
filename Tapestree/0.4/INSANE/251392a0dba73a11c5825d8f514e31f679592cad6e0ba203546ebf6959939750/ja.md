```
sim_gbmpb(t   ::Float64;
          λ0  ::Float64 = 1.0,
          α   ::Float64 = 0.0,
          σλ  ::Float64 = 0.1,
          δt  ::Float64 = 1e-3,
          nlim::Int64   = 10_000,
          init::Symbol  = :crown)
```

時間 `t` で停止する条件付きの純出生幾何ブラウン運動に従って `iTpb` をシミュレートします。
