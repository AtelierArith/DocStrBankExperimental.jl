```
rmeval(NUM,DEN,val) -> Rval
```

Evaluate the rational matrix `R(λ) := NUM(λ)./DEN(λ)` for `λ = val`. 

`NUM(λ)` is a polynomial matrix of the form `NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`, for which   the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `N`,  where `N[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

`DEN(λ)` is a polynomial matrix of the form `DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`, for which  the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `D`,  where `D[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `NUM(λ)` and `DEN(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.
