```
lseval(A, E, B, C, D, val; atol1, atol2, rtol, fast = true) -> Gval
```

Evaluate `Gval`, the value of the rational matrix `G(λ) = C*inv(λE-A)*B+D` for `λ = val`.  The computed `Gval` has infinite entries if `val` is a pole (finite or infinite) of `G(λ)`. If `val` is finite and `val*E-A` is singular or if `val = Inf` and `E` is singular,  then the entries of `Gval` are evaluated separately for minimal realizations of each input-output channel.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`. 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.
