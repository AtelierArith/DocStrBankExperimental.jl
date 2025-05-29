```
insane_gbmct(tree    ::sT_label;
             λ0_prior::NTuple{2,Float64}     = (0.05, 148.41),
             α_prior ::NTuple{2,Float64}     = (0.0, 1.0),
             σλ_prior::NTuple{2,Float64}     = (0.05, 0.05),
             ϵ_prior ::NTuple{2,Float64}     = (0.0, 10.0),
             niter   ::Int64                 = 1_000,
             nthin   ::Int64                 = 10,
             nburn   ::Int64                 = 200,
             nflush  ::Int64                 = nthin,
             ofile   ::String                = string(homedir(), "/ict"),
             tune_int::Int64                 = 100,
             αi      ::Float64               = 0.0,
             λi      ::Float64               = NaN,
             σλi     ::Float64               = 0.01,
             ϵi      ::Float64               = 0.2,
             ϵtni    ::Float64               = 0.1,
             obj_ar  ::Float64               = 0.234,
             pupdp   ::NTuple{5,Float64}     = (1e-3, 1e-3, 1e-4, 0.1, 0.2),
             ntry    ::Int64                 = 2,
             nlim    ::Int64                 = 500,
             δt      ::Float64               = 1e-3,
             prints  ::Int64                 = 5,
             survival::Bool                  = true,
             mxthf   ::Float64               = Inf,
             tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

GBMの出生-死亡のためにinsaneを実行します。
