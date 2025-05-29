```
S = fditspec(sysr::FDFilterIF; FDfreq = missing, block = false, poleshift = false, 
             FDtol, FDStol, atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

Compute the weak or strong binary structure matrix `S` of the transfer function matrix `Rf(λ)` of  the transfer channel from the fault inputs to residuals of  a fault detection filter internal form object `sysr::FDFilterIF`.   For a filter `sysr` with `q` residual outputs and `mf` fault inputs,  `Rf(λ)` is the `q x mf` transfer function matrix of the fault inputs channel with the descriptor system representation `sysr.sys[:,sysr.faults] := (Af-lambda*Ef,Bf,Cf,Df)`. 

If `FDfreq = missing` (default), then `S` contains the weak structure matrix of `Rf(λ)`.  For `block = false`, `S` is determined as a `q x mf`  binary matrix (BitMatrix), whose `(i,j)`-th element is `S[i,j] = 1`, if the `(i,j)`-th element of `Rf(λ)` is  nonzero, and otherwise, `S[i,j] = 0`.  For `block = true`, `S` is determined as a `1 x mf` binary matrix, whose `(1,j)`-th element is `S[1,j] = 1`,  if the `j`-th column of `Rf(λ)` is nonzero, and otherwise, `S[1,j] = 0`. 

If `FDfreq = freq` specifies a vector `freq` of `nf` real frequencies  which characterize the classes of persistent fault signals, then  for a suitable proper and invertible `M(λ)` (see below),   `S` contains the strong structure matrix of `M(λ)*Rf(λ)` with respect to a set of `nf` complex frequencies `Ω`, defined as follows:  if `f` is a real frequency in `freq`, then the corresponding complex frequency in `Ω`  is `λ := im*f`, for a continuous-time system, or `λ := exp(im*f*abs(Ts))`, for a discrete-time system with sampling-time `Ts`. 

`FDtol = tol1` specifies an absolute threshold `tol1` for the magnitudes of nonzero elements in the system matrices  `Bf` and `Df` and is used to determine the weak structure matrix.  Its default value is `tol1 = 0.0001*max(1, norm(Bf,1), norm(Df,1))`. 

`FDStol = tol2` specifies an absolute  threshold `tol2` for the magnitudes of nonzero elements in the system matrices  `Af`, `Ef`, `Bf`, `Cf` and `Df` and is used to determine the strong structure matrix.  Its default value is  `tol2 = epsm*max(1, norm(Ef,1), norm(Af,1), norm(Bf,1), norm(Cf,Inf), norm(Df,1)))`,  where `epsm` is the working machine precision.

For `block = false`, then, if `poleshift = true`, `M(λ)` is chosen diagonal such that `M(λ)*Rf(λ)` has no poles in `Ω` and if `poleshift = false` (default), `M(λ) = I` is used and  an error is issued if `Rf(λ)` has poles in `Ω`.  `S` is determined as a `q x mf` binary matrix, whose `(i,j)`-th element is `S[i,j] = 1`,  if the `(i,j)`-th element of `M(λ)*Rf(λ)`  evaluated for all frequencies in `Ω` is nonzero, and otherwise, `S[i,j] = 0`.  

For `block = true`, then, if `poleshift = true`, `M(λ)` is chosen such that `M(λ)*Rf(λ)`  as no poles in `Ω` and if `poleshift = false` (default), `M(λ) = I` is used and  an error is issued if `Rf(λ)` has poles in `Ω`.  `S` is determined as an `1 x mf` binary matrix, whose `(1,j)`-th element is `S[1,j] = 1`,  if the `j`-th column of `M(λ)*Rf(λ)` evaluated for all frequencies in `Ω` is nonzero and otherwise `S[1,j] = 0`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Af`, `Bf`, `Cf`, `Df`, the absolute tolerance for the nonzero elements of `Ef`,   and the relative tolerance for the nonzero elements of `Af`, `Bf`, `Cf`, `Df` and `Ef`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

*Method:* For the definition of the structure matrix, see [1]. For the determination of the weak structure matrix, minimal realizations are determined for each column of `Rf(λ)` if `block = true` or for  each element of `Rf(λ)` if `block = false` and the nonzero columns or  elements in each column are identified  (see Corollary 7.1 of [1]). For the determination of the strong structure matrix, minimal realizations are determined for each column of `M(λ)*Rf(λ)` if `block = true` or for  each element of `M(λ)*Rf(λ)` if `block = false` and  the full rank of the corresponding system matrix is checked for all frequencies in `FDfreq` (see Corollary 7.2 in [1]) (i.e., the lack of zeros in all frequencies).

*References:*

[1] Varga A. Solving Fault Diagnosis Problems - Linear Synthesis Techniques. Springer Verlag, 2017; sec.3.4.
