```
pmdeg(P) -> deg
```

Determine the degree `deg` of a polynomial matrix `P(λ)`. 

`P(λ)` is a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`, for which  the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`).  The degree of `P(λ)` is `deg = j-1`, where `j` is the largest index for which `P[:,:,j]` is nonzero. The degree of    the zero polynomial matrix is defined to be `deg = -1`.

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.    The degree of `P(λ)` is the largest degree of the elements of `P(λ)`.  The degree of the zero polynomial matrix is defined to be `-1`.
