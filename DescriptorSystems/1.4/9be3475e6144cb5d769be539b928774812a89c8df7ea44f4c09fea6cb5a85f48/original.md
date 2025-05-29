```
isstable(sys[, smarg]; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ, offset = sqrt(ϵ))
```

Return `true` if the descriptor system `sys = (A-λE,B,C,D)` has only stable poles and `false` otherwise.  

It is checked that the pole pencil `P(λ) := A-λE` has no infinite eigenvalues or, if infinite eigenvalues exist, all infinite eigenvalues are simple, and additionally the real parts of all finite eigenvalues  are less than `smarg-β` for a continuous-time system or  have moduli less than `smarg-β` for a discrete-time system, where `smarg` is the stability margin and  `β` is the stability domain boundary offset.  The default value of the stability margin `smarg` is `0` for a continuous-time system and  `1` for a discrete-time system. The offset  `β` to be used to numerically assess the stability of eigenvalues  can be specified via the keyword parameter `offset = β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

For `E` singular, the computation of the poles is performed by reducing the pencil `P(λ)` to an appropriate Kronecker-like form   using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of `A` and `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
