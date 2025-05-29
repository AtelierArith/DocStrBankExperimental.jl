```
gss2ss(sys; Eshape = "ident", atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ) -> (sysr, r)
```

Convert the descriptor system `sys = (A-λE,B,C,D)` to an input-output equivalent descriptor system realization  `sysr = (Ar-λEr,Br,Cr,Dr)` without non-dynamic modes and having the same transfer function matrix. The resulting `Er` is in the SVD-like form `Er = blockdiag(E1,0)`, with `E1` an `r × r` nonsingular matrix,  where `r` is the rank of `E`.

The keyword argument `Eshape` specifies the shape of `E1` as follows:

if `Eshape = "ident"` (the default option), `E1` is an identity matrix of order `r` and if `E` is nonsingular,  then the resulting system `sysr` is a standard state-space system;

if `Eshape = "diag"`, `E1` is a diagonal matrix of order `r`, where the diagonal elements are the  decreasingly ordered nonzero singular values of `E`;

if `Eshape = "triu"`, `E1` is an upper triangular nonsingular matrix of order `r`. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

If `Eshape = "triu"`, the reductions of `E` and `A` are performed using rank decisions based on rank revealing  QR-decompositions with column pivoting.  If `Eshape = "ident"` or `Eshape = "diag"` the reductions are performed using the more reliable SVD-decompositions.
