```
 S = mdspec(sysR::MDFilterIF; cdinp = false, atol, atol1 = atol, atol2 = atol, rtol = 0)
```

Compute the weak binary structure matrix `S`  of a collection of model detection filters using the model detection filter internal form object `sysR::MDFilterIF`.

For an `M × N` array of filters `sysR`, `S` is an `M × N` binary array determined as follows.  Let the `(i,j)`-th component filter `sysR.sys[i,j]` have the input-output form

```
 rij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,
```

with the Laplace- or Z-transformed residual output `rij`, control inputs `u`,  disturbance inputs `dj`, noise inputs `wj`, and auxiliary inputs `vj`,   and with `Ruij(λ)`, `Rdij(λ)`, `Rwij(λ)` and `Rvij(λ)`, the corresponding transfer function matrices.  Then, `S[i,j] = 1` if `Ruij(λ)` is nonzero for `cdinp = false` (default), or if `[Ruij(λs) Rdij(λs)]` is nonzero for `cdinp = true`. Otherwise, `S[i,j] = 0`.

If `(Arij-λErij,Brij,Crij,Drij)` is the descriptor realization of `sysR.sys[i,j]`, then  the keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `Arij`, `Brij`, `Crij`, `Drij`, the absolute tolerance for the nonzero elements of `Erij`,   and the relative tolerance for the nonzero elements of `Arij`, `Brij`, `Crij`, `Drij` and `Eirj`. The default relative tolerance is `nij*ϵ`, where `ϵ` is the working *machine epsilon*  and `nij` is the order of the system matrix of `sysR.sys[i,j]`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
