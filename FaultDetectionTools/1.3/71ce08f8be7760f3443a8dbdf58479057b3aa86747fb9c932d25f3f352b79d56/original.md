```
 S = mdsspec(sysR::MDFilterIF, freq; cdinp = false, MDGainTol = 0.01, 
             atol, atol1 = atol, atol2 = atol, rtol = 0, fast = true)
```

Compute, for a given set of real frequencies `freq`, the strong binary structure matrix `S`  of a collection of model detection filters using the model detection filter internal form object `sysR::MDFilterIF`.

`freq` must contain a real frequency value or a vector of `nf` real frequencies  which characterize the classes of persistent control and disturbance signals  (default: `freq = 0`, i.e., characterizing constant signals) and defines  the set `Ω` of complex frequencies which characterize the classes of persistent signals as follows:  if `f` is a real frequency in `freq`, then the corresponding complex frequency `λ` in `Ω`  is `λ := im*f`, for a continuous-time system, or `λ := exp(im*f*abs(Ts))`, for a discrete-time system with sampling-time `Ts`. 

For an `M × N` array of filters `sysR`, `S` is an `M × N` binary array determined as follows.  Let the `(i,j)`-th component filter `sysR.sys[i,j]` have the input-output form

```
 rij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,
```

with the Laplace- or Z-transformed residual output `rij`, control inputs `u`,  disturbance inputs `dj`, noise inputs `wj`, and auxiliary inputs `vj`,   and with `Ruij(λ)`, `Rdij(λ)`, `Rwij(λ)` and `Rvij(λ)`, the corresponding transfer function matrices.  Then, `S[i,j] = 1` if `Ruij(λs)` is nonzero for any `λs ∈ Ω` and `cdinp = false` (default), or if `[Ruij(λs) Rdij(λs)]` is nonzero for any `λs ∈ Ω` and `cdinp = true`. Otherwise, `S[i,j] = 0`.

`MDGainTol = tol` specifies an absolute  threshold `tol` for the nonzero magnitudes of  the frequency response gains (default: `tol = 0.01`). 

The computation of minimal realizations of individual input-output channels relies on pencil manipulation algorithms, which employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true` (default) or  the more reliable SVD-decompositions if `fast = false`.

If `(Arij-λErij,Brij,Crij,Drij)` is the descriptor realization of `sysR.sys[i,j]`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Arij`, `Brij`, `Crij`, `Drij`, the absolute tolerance for the nonzero elements of `Erij`,   and the relative tolerance for the nonzero elements of `Arij`, `Brij`, `Crij`, `Drij` and `Eirj`. The default relative tolerance is `nij*ϵ`, where `ϵ` is the working *machine epsilon*  and `nij` is the order of the system `sysR.sys[i,j]`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
