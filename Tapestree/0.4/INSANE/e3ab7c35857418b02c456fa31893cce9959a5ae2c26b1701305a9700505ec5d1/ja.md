```
insane_cfbd(tree    ::sTf_label;
            λ_prior ::NTuple{2,Float64}     = (1.0, 1.0),
            μ_prior ::NTuple{2,Float64}     = (1.0, 1.0),
            ψ_prior ::NTuple{2,Float64}     = (1.0, 1.0),
            ψ_epoch ::Vector{Float64}       = Float64[],
            f_epoch ::Vector{Int64}         = Int64[0],
            niter   ::Int64                 = 1_000,
            nthin   ::Int64                 = 10,
            nburn   ::Int64                 = 200,
            nflush  ::Int64                 = nthin,
            ofile   ::String                = string(homedir(), "/cfbd"),
            ϵi      ::Float64               = 0.4,
            λi      ::Float64               = NaN,
            μi      ::Float64               = NaN,
            ψi      ::Float64               = NaN,
            pupdp   ::NTuple{4,Float64}     = (1e-4, 1e-4, 1e-4, 0.2),
            survival::Bool                  = true,
            prints  ::Int64                 = 5,
            mxthf   ::Float64               = Inf,
            tρ      ::Dict{String, Float64} = Dict("" => 1.0))
```

定常的な化石化した出生-死亡のためにinsaneを実行します。
