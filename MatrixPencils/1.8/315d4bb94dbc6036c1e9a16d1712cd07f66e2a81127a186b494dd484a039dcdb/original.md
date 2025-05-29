```
pm2poly(P[,var = 'x']) -> PM
```

Build the polynomial matrix `PM(λ)` from its matrix polynomial representation `P(λ)`. 

`P(λ)` is a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`, for which  the coefficient matrices `P_l`, `l = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,l]` contains the `l`-th coefficient matrix `P_l` (multiplying `λ**(l-1)`). 

`PM(λ)` is a matrix of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  The element `(i,j)` of `PM(λ)` is built from the coefficients contained in `P[i,j,1:k+1]`. The symbol to be used for the indeterminate `λ` can be specified in the optional input variable `var`. 
