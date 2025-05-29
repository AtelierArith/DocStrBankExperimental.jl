```
sim_shift(n       ::Int64;
          λ0      ::Float64 = 1.0,
          μ0      ::Float64 = 0.1,
          pshift  ::Float64 = 0.1,
          σλ      ::Float64 = 0.4,
          start   ::Symbol  = :stem,
          δt      ::Float64 = 1e-3,
          nstar   ::Int64   = 2*n,
          p       ::Float64 = 5.0,
          warnings::Bool    = true,
          maxt    ::Float64 = δt*1e7)
```

`iTbd`を種分化率のシフトモデルに従ってシミュレートします。
