```
insane_gbmbd(tree    ::sT_label;
             λ0_prior::NTuple{2,Float64}     = (0.05, 148.41),
             μ0_prior::NTuple{2,Float64}     = (0.05, 148.41),
             α_prior ::NTuple{2,Float64}     = (0.0, 1.0),
             σλ_prior::NTuple{2,Float64}     = (0.05, 0.05),
             σμ_prior::NTuple{2,Float64}     = (3.0, 0.1),
             niter   ::Int64                 = 1_000,
             nthin   ::Int64                 = 10,
             nburn   ::Int64                 = 200,
             nflush  ::Int64                 = nthin,
             ofile   ::String                = string(homedir(), "/ibd"),
             ϵi      ::Float64               = 0.2,
             λi      ::Float64               = NaN,
             μi      ::Float64               = NaN,
             αi      ::Float64               = 0.0,
             σλi     ::Float64               = 0.01,
             σμi     ::Float64               = 0.01,
             pupdp   ::NTuple{5,Float64}     = (1e-3, 1e-3, 1e-4, 0.1, 0.2),
             δt      ::Float64               = 1e-3,
             survival::Bool                  = true,
             mxthf   ::Float64               = 0.1,
             prints  ::Int64                 = 5,
             stnλ    ::Float64               = 0.5,
             stnμ    ::Float64               = 0.5,
             tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

Run insane for `bdd`.
