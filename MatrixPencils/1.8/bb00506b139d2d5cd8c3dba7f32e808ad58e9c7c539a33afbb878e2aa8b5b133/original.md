```
   pmrank(P; fastrank = true, atol = 0, rtol = atol > 0 ? 0 : n*ϵ)
```

Determine the normal rank of a polynomial matrix `P(λ)`. 

`P(λ)` is a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`, for which  the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). The normal rank of `P(λ)` is the number of linearly independent rows or columns. 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

If `fastrank = true`, the rank is evaluated by counting how many singular values of `P(γ)` have magnitude greater  than `max(atol, rtol*σ₁)`, where `σ₁` is the largest singular value of `P(γ)` and `γ` is a randomly generated  complex value of magnitude equal to one.  If `fastrank = false`, first a structured linearization of `P(λ)` is built in the form `[A-λE B; C D]` with `A-λE` an order `n` regular subpencil, and then its normal rank `nr` is determined. The normal rank of `P(λ)` is `nr - n`.  

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of `P(λ)`. The default relative tolerance is `n*ϵ`, where `n` is the size of the  smallest dimension of `P(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 
