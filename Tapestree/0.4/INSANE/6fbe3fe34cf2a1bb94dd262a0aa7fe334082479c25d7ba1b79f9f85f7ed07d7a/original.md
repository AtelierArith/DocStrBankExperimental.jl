```
insane_cpb(tree    ::sT_label;
           λ_prior ::NTuple{2,Float64}     = (1.0, 1.0),
           niter   ::Int64                 = 1_000,
           nthin   ::Int64                 = 10,
           nburn   ::Int64                 = 200,
           nflush  ::Int64                 = nthin,
           ofile   ::String                = string(homedir(), "/cpb"),
           λi      ::Float64               = NaN,
           pupdp   ::NTuple{2,Float64}     = (0.2, 0.2),
           prints  ::Int64                 = 5,
           tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

Run insane for constant pure-birth.
