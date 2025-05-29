```
poly2pm(PM; grade = k) -> P
```

Build a grade `k` matrix polynomial representation `P(λ)` from a polynomial matrix, polynomial vector or scalar polynomial `PM(λ)`. 

`PM(λ)` is a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

`P(λ)` is a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`, for which  the coefficient matrices `P_l`, `l = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,l]` contains the `l`-th coefficient matrix `P_l` (multiplying `λ**(l-1)`).  If `grade = missing`, then `k` is chosen the largest degree of the elements of `PM`. The coefficients of the degree `d` element `(i,j)` of `PM(λ)` result in `P[i,j,1:d+1]`.
