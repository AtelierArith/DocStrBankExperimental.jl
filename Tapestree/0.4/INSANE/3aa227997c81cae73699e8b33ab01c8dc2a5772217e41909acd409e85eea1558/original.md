```
insane_cbd(tree    ::sT_label;
           λ_prior ::NTuple{2,Float64}     = (1.0, 1.0),
           μ_prior ::NTuple{2,Float64}     = (1.0, 1.0),
           niter   ::Int64                 = 1_000,
           nthin   ::Int64                 = 10,
           nburn   ::Int64                 = 200,
           nflush  ::Int64                 = nthin,
           ofile   ::String                = string(homedir(), "/cbd"),
           ϵi      ::Float64               = 0.4,
           λi      ::Float64               = NaN,
           μi      ::Float64               = NaN,
           pupdp   ::NTuple{3,Float64}     = (1e-4, 1e-4, 0.2),
           prints  ::Int64                 = 5,
           survival::Bool                  = true,
           mxthf   ::Float64               = Inf,
           tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

Run insane for constant birth-death.
