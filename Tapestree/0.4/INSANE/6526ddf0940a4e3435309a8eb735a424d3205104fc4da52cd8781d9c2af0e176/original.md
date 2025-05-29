```
insane_gbmpb(tree    ::sT_label;
             λ0_prior::NTuple{2,Float64}     = (0.05, 148.41),
             α_prior ::NTuple{2,Float64}     = (0.0, 1.0),
             σλ_prior::NTuple{2,Float64}     = (3.0, 0.5),
             niter   ::Int64                 = 1_000,
             nthin   ::Int64                 = 10,
             nburn   ::Int64                 = 200,
             nflush  ::Int64                 = nthin,
             ofile   ::String                = string(homedir(), "/ipb"),
             αi      ::Float64               = 0.0,
             σλi     ::Float64               = 0.1,
             pupdp   ::NTuple{5,Float64}     = (1e-3, 1e-3, 1e-3, 0.2, 0.2),
             δt      ::Float64               = 1e-3,
             prints  ::Int64                 = 5,
             stn     ::Float64               = 0.5,
             tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

Run insane for `pbd`.
