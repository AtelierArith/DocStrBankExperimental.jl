```
 S = fdisspec(sysr::FDFilterIF, freq; block = false, stabilize = false, FDGainTol = 0.01, 
                 atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

Compute, for a given set of real frequencies `freq`,   the strong binary structure matrix `S` of the stable transfer function matrix `M(λ)*Rf(λ)`,  where `Rf(λ)` is the transfer function matrix of the transfer channel from the fault inputs to residuals of the fault detection filter internal form object `sysr::FDFilterIF` and   `M(λ)` is a suitable proper and invertible stabilizing transfer function matrix (see below).   For a filter `sysr` with `q` residual outputs and `mf` fault inputs,  `Rf(λ)` is the `q x mf` transfer function matrix of the fault inputs channel with the descriptor system representation `sysr.sys[:,sysr.faults] := (Af-lambda*Ef,Bf,Cf,Df)`. 

`freq` must contain a real frequency value or a vector of `nf` real frequencies  which characterize the classes of persistent fault signals  (default: `freq = 0`, i.e., characterizing constant faults). `S` contains the strong  structure matrix of `M(λ)*Rf(λ)` with respect to a set of `nf` complex frequencies `Ω`, defined as follows:  if `f` is a real frequency in `freq`, then the corresponding complex frequency in `Ω`  is `λ := im*f`, for a continuous-time system, or `λ := exp(im*f*abs(Ts))`, for a discrete-time system with sampling-time `Ts`.  

`FDGainTol = tol` specifies an absolute  threshold `tol` for the nonzero magnitudes of  the frequency response gains (default: `tol = 0.01`). 

For `block = false`, then, if `stabilize = true`, `M(λ)` is chosen diagonal such that `M(λ)*Rf(λ)` has only stable poles and if `stabilize = false` (default), `M(λ) = I` is used and  an error is issued if `Rf(λ)` has poles in `Ω`.  `S` is determined as a `q x mf` binary matrix, whose `(i,j)`-th element is `S[i,j] = 1`,  if the `(i,j)`-th element of `M(λ)*Rf(λ)`  evaluated for all frequencies in `freq` is larger than or equal to `tol`, and otherwise, `S[i,j] = 0`.  

For `block = true`, then, if `stabilize = true`, `M(λ)` is chosen such that `M(λ)*Rf(λ)`  has only stable poles and if `stabilize = false` (default), `M(λ) = I` is used and  an error is issued if `Rf(λ)` has poles in `Ω`.  `S` is determined as an `1 x mf` binary matrix, whose `(1,j)`-th element is `S[1,j] = 1`,  if the `j`-th column of `M(λ)*Rf(λ)` evaluated for all frequencies in `Ω` is larger than or equal to `tol` and otherwise, `S[1,j] = 0`. 

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Af`, `Bf`, `Cf`, `Df`, the absolute tolerance for the nonzero elements of `Ef`,  the absolute tolerance for the nonzero elements of `Cf`,    and the relative tolerance for the nonzero elements of `Af`, `Bf`, `Cf`, `Df` and `Ef`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

*Method:* `S` is evaluated using the definition of the strong structure matrix in [1]. 

*References:*

[1] Varga A. Solving Fault Diagnosis Problems - Linear Synthesis Techniques. Springer Verlag, 2017; sec. 3.4.
