```
ls2rm(A, E, B, C, D; fast = true, atol1 = 0, atol2 = 0, gaintol = 0, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val) -> (NUM, DEN)
```

Build the rational matrix `R(λ) = C*inv(λE-A)*B+D := NUM(λ) ./ DEN(λ)` corresponding to its structured linearization 

```
        | A-λE | B | 
 S(λ) = |------|---|
        |  C   | D |
```

by explicitly determining for each rational entry of `R(λ)`, its numerator coefficients from its finite zeros and gain, and  its denominator coefficients from its finite poles (see [1]). 

The keyword arguments `atol1` and `atol2` specify the absolute tolerances for the elements of `A`, `B`, `C`, `D`, and,   respectively, of `E`, and `rtol` specifies the relative tolerances for the nonzero elements of `A`, `B`, `C`, `D` and `E`. The default relative tolerance is `(n+1)*ϵ`, where `n` is the dimension of `A`, and `ϵ` is the  machine epsilon of the element type of coefficients of `A`. 

The keyword argument `gaintol` specifies the threshold for the magnitude of the nonzero elements of the gain matrix  `C*inv(γE-A)*B+D`, where `γ = val` if `val` is a number or `γ` is a randomly chosen complex value of unit magnitude,  if `val = missing`. Generally, `val` should not be a zero of any of entries of `R`.

`NUM(λ)` is a polynomial matrix of the form `NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`, for which   the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `NUM`,  where `NUM[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

`DEN(λ)` is a polynomial matrix of the form `DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`, for which  the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `DEN`,  where `DEN[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

[1] A. Varga Computation of transfer function matrices of generalized state-space models.      Int. J. Control, 50:2543–2561, 1989.
