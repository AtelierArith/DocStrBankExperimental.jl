```
rm2lspm(NUM, DEN; contr = false, obs = false, atol = 0, rtol) -> (A, B, C, D, blkdims)
```

Construct a representation of the rational matrix `R(λ) := NUM(λ)./DEN(λ)` as the sum of its strictly proper part,   realized as a structured linearization 

```
          | A-λI | B | 
          |------|---|
          |  C   | 0 |
```

and its polynomial part `D(λ)`. The resulting representation satisfies 

```
 R(λ) = C*inv(λI-A)*B + D(λ).
```

The linearization `(A-λI,B,C,0)` of the strictly proper part is in general non-minimal.  A controllable realization is constructed if `contr = true`, while an observable realization results if `obs = true`.  The matrix `A` results block diagonal and the vector `blkdims` contains the sizes of the diagonal blocks of `A`, such that the size of the `i`-th diagonal block is provided in `blkdims[i]`. See [1] for details. 

`NUM(λ)` is a polynomial matrix of the form `NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`, for which   the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `NUM`,  where `NUM[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

`DEN(λ)` is a polynomial matrix of the form `DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`, for which  the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `DEN`,  where `DEN[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `NUM(λ)` and `DEN(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.

The polynomial part `D(λ)` is contained in `D`, which is a 2-dimensional array if `D(λ)` has degree 0 or a 3-dimensional array if `D(λ)` has degree  greater than 0. In the latter case `D[:,:,i]` contains the `i`-th  coefficient matrix multiplying `λ**(i-1)`. 

The keyword arguments `atol` and `rtol`, specify the absolute and relative tolerances for the  nonzero coefficients of `DEN(λ)`, respectively.  

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
