```
ghanorm(sys, fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (hanorm, hs)
```

Compute for a proper and stable descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`, the Hankel norm `hanorm =` $\small ||G(\lambda)||_H$ and  the vector of Hankel singular values `hs` of the minimal realizatioj of the system.

For a non-minimal system, the uncontrollable and unobservable finite and infinite eigenvalues of the pair `(A,E)` and the non-dynamic modes are elliminated using minimal realization techniques. The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 
