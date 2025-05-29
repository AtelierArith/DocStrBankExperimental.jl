```
Gval = evalfr(sys; fval = 0, atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

Evaluate for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`, `Gval`, the value of the rational matrix `G(λ) = C*inv(λE-A)*B+D` for `λ = val`, where `val = im*fval`  for a continuous-time system or `val = exp(im*fval*sys.Ts)` for a discrete-time system.  The computed `Gval` has infinite entries if `val` is a pole (finite or infinite) of `G(λ)`. If `val` is finite and `val*E-A` is singular or if `val = Inf` and `E` is singular,  then the entries of `Gval` are evaluated separately for minimal realizations of each input-output channel.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`. The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.
