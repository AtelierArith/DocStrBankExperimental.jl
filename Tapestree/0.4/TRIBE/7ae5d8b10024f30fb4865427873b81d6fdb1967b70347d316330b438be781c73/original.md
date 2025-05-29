```
tribe(tip_values::Dict{Int64,Float64}, 
      tip_areas ::Dict{Int64,Array{Int64,1}},
      tree      ::rtree, 
      bts       ::Array{Float64,1},
      out_file  ::String;
      min_dt    ::Float64           = 0.01,
      niter     ::Int64             = 500_000,
      nburn     ::Int64             = 500_000,
      nthin     ::Int64             = 1_000,
      saveXY    ::Tuple{Bool,Int64} = (false, 1_000),
      saveDM    ::Tuple{Bool,Int64} = (false, 1_000),
      ωxprior   ::NTuple{2,Float64} = (0.,10.),
      ω1prior   ::NTuple{2,Float64} = (0.,10.),
      ω0prior   ::NTuple{2,Float64} = (0.,10.),
      σ²prior   ::Float64           = 1e-1,
      λprior    ::Float64           = 1e-1,
      weight    ::NTuple{5,Float64} = (0.15,0.05,0.02,0.02,5e-3),
      λ1i       ::Float64           = 1.0,
      λ0i       ::Float64           = 0.4,
      ωxi       ::Float64           = 0.,
      ω1i       ::Float64           = 0.,
      ω0i       ::Float64           = 0.,
      fix_ωx    ::Bool              = false,
      fix_ω1    ::Bool              = false,
      fix_ω0    ::Bool              = false,
      delim     ::Char              = '	',
      eol       ::Char              = '')
```

Run tribe for simulations. Wrapper for all functions.
