```
grm(s, method=:GRM, minmaf=0.01, colinds=nothing)
```

Compute empirical kinship matrix from a SnpArray `s`. Missing genotypes are imputed on the fly by column mean.

# Arguments

  * `method::Symbol=:GRM`: `:GRM` (default), `:MoM`, or `:Robust`.
  * `minmaf::Real=0.01`: columns with MAF less than `minmaf` are excluded; default 0.01.
  * `cinds=nothing`: indices or mask of columns to be used for calculating GRM.
  * `t::Type{T}=Float64`: Float type for calculating GRM; default is `Float64`.
