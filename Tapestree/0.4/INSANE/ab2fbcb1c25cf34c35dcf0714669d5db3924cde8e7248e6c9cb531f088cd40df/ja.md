```
insane_gbmbd(tree    ::sT_label,
             tv      ::Vector{Vector{Float64}},
             ev      ::Vector{Vector{Float64}};
             λ0_prior::NTuple{2,Float64}     = (0.05, 148.41),
             μ0_prior::NTuple{2,Float64}     = (0.05, 148.41),
             α_prior ::NTuple{2,Float64}     = (0.0, 1.0),
             σλ_prior::NTuple{2,Float64}     = (0.05, 0.05),
             σμ_prior::NTuple{2,Float64}     = (3.0, 0.1),
             niter   ::Int64                 = 1_000,
             nthin   ::Int64                 = 10,
             nburn   ::Int64                 = 200,
             nflush  ::Int64                 = nthin,
             ofile   ::String                = string(homedir(), "/ibd_efx"),
             ϵi      ::Float64               = 0.2,
             λi      ::Float64               = NaN,
             αi      ::Float64               = 0.0,
             σλi     ::Float64               = 0.01,
             σμi     ::Float64               = 0.01,
             pupdp   ::NTuple{4,Float64}     = (1e-3, 1e-3, 0.1, 0.2),
             δt      ::Float64               = 1e-3,
             prints  ::Int64                 = 5,
             survival::Bool                  = true,
             mxthf   ::Float64               = 0.1,
             tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

`gbm-bd`を固定絶滅で実行します。
