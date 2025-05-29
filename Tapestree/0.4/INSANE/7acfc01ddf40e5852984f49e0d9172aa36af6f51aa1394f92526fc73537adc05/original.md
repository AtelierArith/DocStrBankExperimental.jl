```
sim_gbmfbd(t   ::Float64;
           λ0  ::Float64         = 1.0,
           μ0  ::Float64         = 0.2,
           αλ  ::Float64         = 0.0,
           αμ  ::Float64         = 0.0,
           σλ  ::Float64         = 0.1,
           σμ  ::Float64         = 0.1,
           ψ   ::Vector{Float64} = [0.1],
           ψts ::Vector{Float64} = Float64[],
           δt  ::Float64         = 1e-3,
           nlim::Int64           = 10_000,
           init::Symbol          = :crown)
```

Simulate `iTfbd` according to geometric Brownian motions for birth and death rates.
