```
sysinv = inv(sys; atol = 0, atol1 = atol, atol2 = atol, rtol, checkinv = true)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`, a descriptor realization of its inverse system `sysinv = (Ai-λEi,Bi,Ci,Di)`, such that the transfer function matrix `Ginv(λ)` of `sysinv` is the inverse of `G(λ)` (i.e., `G(λ)*Ginv(λ) = I`).  The realization of `sysinv` is determined using inversion-free formulas and the invertibility condition is checked, unless `checkinv = false`.

The keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of the square matrices `A` and `E`, and  `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
