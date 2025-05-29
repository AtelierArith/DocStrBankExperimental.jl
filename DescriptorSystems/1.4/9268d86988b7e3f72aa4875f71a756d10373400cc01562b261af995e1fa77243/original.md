```
val = gpole(sys; fast = false, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ)
```

Return for the descriptor system `sys = (A-λE,B,C,D)` the complex vector `val` containing  the finite and infinite zeros of the system pole pencil `P(λ) := A-λE`.  The values in `val` are the poles of the transfer function matrix of `sys`, if `A-λE` is *regular* and the  descriptor system realization `sys = (A-λE,B,C,D)` is *irreducible*.  If the pencil `A-λE` is singular, `val` also contains `NaN` elements, whose number is the rank deficiency of the pencil  `A-λE`.

For `E` nonsingular, `val` contains the generalized eigenvalues of the pair `(A,E)`.  For `E` singular, `val` contains the zeros of `P(λ)`, which are computed  by reducing the pencil `P(λ)` to an appropriate Kronecker-like form   using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. 

The regularity of `A-λE` is implicitly checked. If `check_reg = true`, an error message is issued if the pencil    `A-λE` is singular. If `check_reg = false` and the pencil `A-λE` is singular, then `n-r` poles are set to `NaN`, where `n` is the system order and `r` is the normal rank of `A-λE`. 

The keyword arguements `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A` and `E`, respectively.  The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
