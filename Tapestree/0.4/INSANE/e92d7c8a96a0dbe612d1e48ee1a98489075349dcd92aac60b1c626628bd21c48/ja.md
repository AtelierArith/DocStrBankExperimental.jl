```
sim_gbmfbd(n       ::Int64;
           λ0      ::Float64         = 1.0,
           μ0      ::Float64         = 0.2,
           αλ      ::Float64         = 0.0,
           αμ      ::Float64         = 0.0,
           σλ      ::Float64         = 0.1,
           σμ      ::Float64         = 0.1,
           ψ       ::Vector{Float64} = [0.1],
           ψts     ::Vector{Float64} = Float64[],
           init    ::Symbol          = :stem,
           δt      ::Float64         = 1e-3,
           nstar   ::Int64           = 2*n,
           p       ::Float64         = 5.0,
           warnings::Bool            = true,
           maxt    ::Float64         = δt*1e6)
```

出生率と死亡率の幾何ブラウン運動に従って `iTfbd` をシミュレートします。すべての時代に沿って進化するわけではないことに注意してください。
