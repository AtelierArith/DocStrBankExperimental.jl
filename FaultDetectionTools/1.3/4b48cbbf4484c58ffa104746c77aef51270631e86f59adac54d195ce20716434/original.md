```
S = fditspec(sysr::FDIFilterIF; FDfreq = missing, poleshift = false, 
             FDtol, FDStol, atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

Compute the weak or strong binary structure matrix `S` of the global transfer function matrix `Rf(λ)` of  the transfer channel from the fault inputs to residuals of  a fault detection and isolation filter internal form object `sysr::FDIFilterIF`.   The filter `sysr` consists of `N` individual FDI filters `sysr.sys[i]`, for `i = 1, ..., N`, where the fault to residual channel of the `i`-th filter `sysr.sys[i][:,sysr.faults]`  has `qi` residual outputs and `mf` fault inputs, has the descriptor system representation `sysr.sys[i][:,sysr.faults] := (Afi-lambda*Efi,Bfi,Cfi,Dfi)` and  `Rfi(λ)` is the corresponding `qi x mf` transfer function matrix.  The global transfer function matrix `Rf(λ)` is formed by row concatenation of the  transfer function matrices of the `N` individual filters, i.e.,  `Rf(λ) := [ Rf1(λ); Rf2(λ); ...; RfN(λ)]`.  For the evaluation of the strong structure matrix, the structure matrix of the stable  transfer function matrix `M(λ)*Rf(λ)` is determined, with a `M(λ)` block-diagonal `M(λ) = block-diag(M1(λ), M2(λ), ..., MN(λ))`, where `Mi(λ)` is a suitable square and invertible  transfer function matrix (see below). 

`FDtol = tol1` specifies an absolute threshold `tol1` for the magnitudes of nonzero elements in the system matrices  `Bf` and `Df` and is used to determine the weak structure matrix.  Its default value is `tol1 = 0.0001*max(1, norm(Bf,1), norm(Df,1))`. 

`FDStol = tol2` specifies an absolute  threshold `tol2` for the magnitudes of nonzero elements in the system matrices  `Af`, `Ef`, `Bf`, `Cf` and `Df` and is used to determine the strong structure matrix.  Its default value is  `tol2 = epsm*max(1, norm(Ef,1), norm(Af,1), norm(Bf,1), norm(Cf,Inf), norm(Df,1)))`,  where `epsm` is the working machine precision.

If `FDfreq = missing` (default), then `S` contains the weak structure matrix of `Rf(λ)`.  `S` is determined as a `N x mf` binary matrix, whose `(i,j)`-th element is `S[i,j] = 1`,  if the `j`-th column of `Rfi(λ)` is nonzero, and otherwise, `S[i,j] = 0`. 

If `FDfreq = freq` specifies a vector `freq` of `nf` real frequencies  which characterize the classes of persistent fault signals, then  for a suitable proper and invertible `M(λ)` (see below),   `S` contains the strong structure matrix of `M(λ)*Rf(λ)` with respect to a set of `nf` complex frequencies `Ω`, defined as follows:  if `f` is a real frequency in `freq`, then the corresponding complex frequency in `Ω`  is `λ := im*f`, for a continuous-time system, or `λ := exp(im*f*abs(Ts))`, for a discrete-time system with sampling-time `Ts`. 

`S` is determined as a `N x mf` binary matrix, whose `(i,j)`-th element is `S[i,j] = 1`,  if the `j`-th column of `Mi(λ)*Rfi(λ)` is nonzero for all frequencies in `Ω`, and otherwise, `S[i,j] = 0`.  If `poleshift = true`, `Mi(λ)` is chosen such that `Mi(λ)*Rfi(λ)` has no poles in `Ω` and if `poleshift = false` (default), `Mi(λ) = I` is used and an error is issued if any `Rfi(λ)` has poles in `Ω`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Af`, `Bf`, `Cf`, `Df`, the absolute tolerance for the nonzero elements of `Ef`,   and the relative tolerance for the nonzero elements of `Af`, `Bf`, `Cf`, `Df` and `Ef`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

*Method:* For the definition of the structure matrix, see [1]. For the determination of the weak structure matrix, minimal realizations are determined for each column of `Rfi(λ)` and the nonzero columns are identified  (see Corollary 7.1 of [1]). For the determination of the strong structure matrix, minimal realizations are determined for each column of `Mi(λ)*Rfi(λ)` and  the full rank of the corresponding system matrix is checked for all frequencies in `Ω` (see Corollary 7.2 in [1]) (i.e., the lack of zeros in all frequencies in `Ω`).

*References:*

[1] Varga A. Solving Fault Diagnosis Problems - Linear Synthesis Techniques. Springer Verlag, 2017; sec.3.4.
