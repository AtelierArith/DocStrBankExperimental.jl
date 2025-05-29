```
tribe(out_file::String;
      niter   ::Int64             = 500_000,
      nburn   ::Int64             = 500_000,
      nthin   ::Int64             = 1_000,
      ωxprior ::NTuple{2,Float64} = (0.,10.),
      ω1prior ::NTuple{2,Float64} = (0.,10.),
      ω0prior ::NTuple{2,Float64} = (0.,10.),
      σ²prior ::Float64           = 1e-1,
      λprior  ::Float64           = 1e-1,
      weight  ::NTuple{4,Float64} = (0.15,0.05,0.02,0.02),
      σ²i     ::Float64           = 1.,
      ωxi     ::Float64           = 0.,
      ω1i     ::Float64           = 0.01,
      ω0i     ::Float64           = 0.01,
      λ1i     ::Float64           = 1.0,
      λ0i     ::Float64           = 0.2,
      fix_ωx  ::Bool              = false,
      fix_ω1  ::Bool              = false,
      fix_ω0  ::Bool              = false)
```

Run tribe **under the prior**. Wrapper for all functions.
