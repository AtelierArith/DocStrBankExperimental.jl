```
pmroots(P; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> val
```

Compute the roots of the determinant of the regular polynomial matrix `P(λ)` in `val`. 

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The roots of `det(P(λ))` are computed as the finite eigenvalues of a companion form linearization `M-λN`of `P(λ)`. The finite eigenvalues are computed by reducing the pencil `M-λN` to an appropriate Kronecker-like form (KLF)  exhibiting the spliting of the infinite and finite eigenvalue structures of the pencil `M-λN`.  The reduction is performed using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `P(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `P(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `P(λ)`. 
