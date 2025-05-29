```
Gval = dcgain(sys; atol1, atol2, rtol, fast = true)
```

Evaluate for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`, `Gval`, the DC (or steady-state) gain. `Gval` is the value of the  rational matrix `G(λ)` for `λ = val`, where for a continuous-time system `val = 0` and  for a discrete-time system `val = 1`. The computed `Gval` has infinite entries if `val` is a pole of `G(λ)`. In this case (i.e., `val*E-A` is singular), the entries of `Gval` are evaluated separately for minimal realizations  of each input-output channel.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`. 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation  algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.
