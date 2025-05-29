```
pmreverse(P[,j]) -> Q
```

Build `Q(λ) = λ^j*P(1/λ)`, the `j`-reversal of a polynomial matrix `P(λ)` for `j ≥ deg(P(λ))`.  If `j` is not specified, the default value `j = deg(P(λ))` is used. 

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

If deg(P(λ)), then `Q(λ)` is a grade `j` polynomial matrix of the form  `Q(λ) = Q_1 + λ Q_2 + ... + λ**j Q_(j+1)`, for which  the coefficient matrices `Q_i`, `i = 1, ..., j+1`, are stored in the 3-dimensional matrix `Q`,  where `Q[:,:,i]` contains the `i`-th coefficient matrix `Q_i` (multiplying `λ**(i-1)`).  The coefficient matrix `Q_i` is either `0` if `i ≤ j-d` or `Q_(j-d+i) = P_(d-i+1)` for `i = 1, ..., d`.
