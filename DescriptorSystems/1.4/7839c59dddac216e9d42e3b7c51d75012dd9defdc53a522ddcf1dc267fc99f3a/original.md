```
 dss2ss(sys[, x0 = 0]; state-mapping = false, simple_infeigs = true, fast = true, atol1, atol2, rtol) 
           -> (sysr, xr0, Mx, Mu)
```

Return for a proper descriptor system `sys = (A-λE,B,C,D)` and initial state `x0`,  the equivalent reduced order standard system `sysr = (Ar-λI,Br,Cr,Dr)` and  the corresponding reduced consistent initial state `xr0`.

If `state_mapping = true`, the state mapping matrices `Mx` and `Mu` are also determined such that  the values `x(t)` and `xr(t)` of the state vectors of the systems `sys` and `sysr`, respectively, and the input vector `u(t)` are related as `x(t) = Mx*xr(t)+Mu*u(t)`. In this case, higher order uncontrollable infinite eigenvalues can be eliminated if `simple_infeigs = false`.

By default, `state_mapping = false` and `Mx = nothing` and `Mu = nothing`.  In this case, higher order uncontrollable or unobservable infinite eigenvalues  can be eliminated if `simple_infeigs = false`. 

By default, `simple_infeigs = true`, and simple infinite eigenvalues for the pair `(A,E)` are assumed and eliminated. 

The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true` (default), or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable,  but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of the square matrices `A` and `E`, and  `ϵ` is the working machine epsilon. 
