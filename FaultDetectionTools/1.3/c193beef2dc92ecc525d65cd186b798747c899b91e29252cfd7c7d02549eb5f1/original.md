```
 S = fdisspec(sysr::FDIFilterIF, freq; stabilize = false, FDGainTol = 0.01, 
                 atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

Compute, for a given set of real frequencies `freq`,   the strong binary structure matrix `S`  of the stable transfer function matrix `M(λ)*Rf(λ)`, where `Rf(λ)` is the global  transfer function matrix of the transfer channel from the fault inputs to residuals of the fault detection and isolation filter internal form object `sysr::FDIFilterIF` and   `M(λ)` is a suitable block-diagonal proper and invertible stabilizing transfer function matrix (see below).   The filter `sysr` consists of `N` individual FDI filters `sysr.sys[i]`, for `i = 1, ..., N`, where the fault to residual channel of the `i`-th filter `sysr.sys[i][:,sysr.faults]`  has `qi` residual outputs and `mf` fault inputs, has the descriptor system representation `sysr.sys[i][:,sysr.faults] := (Afi-lambda*Efi,Bfi,Cfi,Dfi)` and  `Rfi(λ)` is the corresponding `qi x mf` transfer function matrix.  The global transfer function matrix `Rf(λ)` is formed by row concatenation of the  transfer function matrices of the `N` individual filters, i.e.,  `Rf(λ) := [ Rf1(λ); Rf2(λ); ...; RfN(λ)]`.  `M(λ) = block-diag(M1(λ), M2(λ), ..., MN(λ))`, where `Mi(λ)` is square and invertible  and chosen such that `Mi(λ)Rfi(λ)` is stable (see below). 

`freq` must contain a real frequency value or a vector of `nf` real frequencies  which characterize the classes of persistent fault signals  (default: `freq = 0`, i.e., characterizing constant faults). `S` contains the strong  structure matrix of `M(λ)*Rf(λ)` with respect to a set of `nf` complex frequencies `Ω`, defined as follows:  if `f` is a real frequency in `freq`, then the corresponding complex frequency in `Ω`  is `λ := im*f`, for a continuous-time system, or `λ := exp(im*f*abs(Ts))`, for a discrete-time system with sampling-time `Ts`.  

`FDGainTol = tol` specifies an absolute  threshold `tol` for the nonzero magnitudes of  the frequency response gains (default: `tol = 0.01`). 

If `stabilize = true`, `Mi(λ)` is chosen such that `Mi(λ)*Rfi(λ)` has only stable poles and if `stabilize = false` (default), `Mi(λ) = I` is used and an error is issued  if any `Rfi(λ)` has poles in `Ω`. 

`S` is determined as a `N x mf`  binary matrix, whose `(i,j)`-th element is `S[i,j] = 1`, if the norm of the  `j`-th column of `Mi(λ)*Rfi(λ)` evaluated for all frequencies in `Ω`  is larger than or equal to `tol`, and otherwise, `S[i,j] = 0`. 

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Afi`, `Bfi`, `Cfi`, `Dfi`, the absolute tolerance for the nonzero elements of `Efi`,  the absolute tolerance for the nonzero elements of `Cfi`,    and the relative tolerance for the nonzero elements of `Afi`, `Bfi`, `Cfi`, `Dfi` and `Efi`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

*Method:* `S` is evaluated using the definition of the strong structure matrix in [1]. 

*References:*

[1] Varga A. Solving Fault Diagnosis Problems - Linear Synthesis Techniques. Springer Verlag, 2017; sec. 3.4.
