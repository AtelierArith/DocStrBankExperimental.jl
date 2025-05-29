```
pmdivrem(N,D) -> (Q, R)
```

Compute the quotients in `Q(λ)` and remainders in `R(λ)` of the elementwise polynomial divisions `N(λ)./D(λ)`. 

`N(λ)` is a polynomial matrix of the form `N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`, for which   the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `N`,  where `N[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

`D(λ)` is a polynomial matrix of the form `D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`, for which  the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `D`,  where `D[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `N(λ)` and `D(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package. 

The polynomial matrices of quotients `Q(λ)` and remainders `R(λ)` are stored in the 3-dimensional  matrices `Q` and  `R`, respectively, where `Q[:,:,i]` and `R[:,:,i]` contain the `i`-th  coefficient matrix multiplying `λ**(i-1)`. 
