```
l, res = find_lft(sys::StateSpace{<:Any, <:StaticParticles{<:Any, N}}, δ) where N
```

NOTE: This function is experimental. 

Given an systems `sys` with uncertain coefficients in the form of `StaticParticles`, search for a lower linear fractional transformation `M` such that `lft(M, δ) ≈ sys`. 

`δ` can be either the source of uncertainty in `sys`, i.e., a vector of the unique uncertain parameters that were used to create `sys`. These should be constructed as uniform randomly distributed particles for most robust-control theory to be applicable.  `δ` can also be an integer, in which case a numer of `δ` sources of uncertainty are automatically created. This could be used for order reduction if the number of uncertainty sources in `sys` is large.

Note, uncertainty in `sys` is only supported in `A` and `B`, `C` and `D` must be deterministic.

Returns `l::LFT` that internaly contains all four blocks of `M` as well as `δ`. Call `ss(l,sys)` do obtain `lft(M, δ) ≈ sys`.

Call `Matrix(l)` to obtain `M = [M11 M12; M21 M22]`
