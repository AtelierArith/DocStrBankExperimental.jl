```
R = dss2rm(sys; fast = true, atol = 0, atol1 = atol, atol2 = atol, gaintol = atol, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val)
```

Build for the descriptor system `sys = (A-λE,B,C,D)` the rational matrix `R(λ) = C*inv(λE-A)*B+D` representing the  transfer function matrix of the system `sys`.  

The keyword arguments `atol1` and `atol2` specify the absolute tolerances for the elements of `A`, `B`, `C`, `D`, and,   respectively, of `E`, and `rtol` specifies the relative tolerances for the nonzero elements of `A`, `B`, `C`, `D` and `E`. The default relative tolerance is `n*ϵ`, where `n` is the maximal dimension of state, input and output vectors,  and `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol` and `gaintol = atol`. 

The keyword argument `gaintol` specifies the threshold for the magnitude of the nonzero elements of the gain matrix  `C*inv(γE-A)*B+D`, where `γ = val` if `val` is a number or `γ` is a randomly chosen complex value of unit magnitude,  if `val = missing`. Generally, `val` should not be a zero of any of entries of `R`.

*Method:* Each rational entry of `R(λ)` is constructed from its numerator and denominator polynomials corresponding to its finite zeros, finite poles and gain using the method of [1]. 

*References:*

[1] A. Varga Computation of transfer function matrices of generalized state-space models.      Int. J. Control, 50:2543–2561, 1989.
