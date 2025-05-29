```
insane_dbm(tree     ::Tlabel,
           xa       ::Dict{String, Float64};
           xs       ::Dict{String, Float64} = Dict{String,Float64}(),
           αx_prior ::NTuple{2,Float64} = (0.0, 10.0),
           ασ_prior ::NTuple{2,Float64} = (0.0, 10.0),
           γ_prior  ::NTuple{2,Float64} = (0.05, 0.05),
           niter    ::Int64             = 1_000,
           nthin    ::Int64             = 10,
           nburn    ::Int64             = 200,
           nflush   ::Int64             = nthin,
           ofile    ::String            = string(homedir(), "/dbm"),
           αi       ::Float64           = 0.0,
           γi       ::Float64           = 1e-3,
           pupdp    ::NTuple{4,Float64} = (0.1, 0.1, 0.05, 0.9),
           δt       ::Float64           = 1e-3,
           stn      ::Float64           = 0.1,
           mxthf    ::Float64           = 0.1,
           prints   ::Int64             = 5)
```

Run diffused Brownian motion trait evolution model.
