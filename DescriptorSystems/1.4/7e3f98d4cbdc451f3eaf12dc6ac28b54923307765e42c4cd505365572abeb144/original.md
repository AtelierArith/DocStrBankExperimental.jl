```
gbilin(sys, g; compact = true, minimal = false, standard = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (syst, ginv)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)` and  a first degree real rational transfer function `g = g(δ)`,  the descriptor system realization `syst = (At-δEt,Bt,Ct,Dt)` of `G(g(δ))` corresponding to the bilinear transformation  `λ = g(δ) = (aδ+b)/(cδ+d)`. For a continuous-time transfer function `g(δ)`, `δ = s`, the complex variable in  the Laplace transform, while for a discrete-time transfer function,   `δ = z`, the complex variable in the `Z`-transform. `syst` inherits the sampling-time of `sys1`.  `sysi1` is the transfer function `ginv(λ) = (d*λ-b)/(-c*λ+a)` representing the inverse of the bilinear transformation `g(δ)`  (i.e., `g(ginv(λ)) = 1`).

The keyword argument `compact` can be used to specify the option to compute a compact descriptor realization without non-dynamic modes, if `compact = true` (the default option) or to disable the ellimination of non-dynamic modes if `compact = false`. 

The keyword argument `minimal` specifies the option to compute minimal descriptor realization, if  `minimal = true`, or a nonminimal realization if `minimal = false` (the default option).

The keyword argument `standard` specifies the  option to compute a standard state-space (if possible) realizations of `syst`, if `standard = true` (default), or a descriptor system realization if `standard = false`.  

The keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of the square matrices `A` and `E`, and  `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
