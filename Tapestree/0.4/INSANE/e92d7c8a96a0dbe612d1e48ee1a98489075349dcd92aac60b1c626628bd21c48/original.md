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

Simulate `iTfbd` according to geometric Brownian motions for birth and death rates. Note that it will not necessarily evolve along all of the epochs.
