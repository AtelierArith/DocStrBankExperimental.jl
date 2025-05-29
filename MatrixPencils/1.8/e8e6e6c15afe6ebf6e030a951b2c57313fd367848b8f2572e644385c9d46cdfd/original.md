```
ispmregular(P; fastrank = true, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> Bool
```

Test whether the polynomial matrix `P(λ)` is regular (i.e., `P(λ)` is square and ${\small\det(P(λ)) \not\equiv 0}$).  The underlying computational procedure checks that the normal rank of the square `P(λ)` is equal to its order.

`P(λ)` is a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`, for which  the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.    f If `fastrank = true`, the rank is evaluated by counting how many singular values of `P(γ)` have magnitude greater  than `max(atol, rtol*σ₁)`, where `σ₁` is the largest singular value of `P(γ)` and `γ` is a randomly generated  complex value of magnitude equal to one.  If `fastrank = false`, first a linearization of `P(λ)` is built in a companion form `M-λN` of order `n`  and then its normal rank `nr` is determined. `P(λ)` is regular if `nr = n`.  

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of `P(λ)`. The default relative tolerance is `n*ϵ`, where `n` is the size of the  smallest dimension of `P(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 
