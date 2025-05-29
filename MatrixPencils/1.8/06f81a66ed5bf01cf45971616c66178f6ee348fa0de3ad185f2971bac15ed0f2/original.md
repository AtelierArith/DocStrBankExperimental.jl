```
ls2pm(A, E, B, C, D; fast = true, atol1 = 0, atol2 = 0, gaintol = 0, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val) -> P
```

Build the polynomial matrix `P(λ) = C*inv(λE-A)*B+D` corresponding to its structured linearization 

```
 | A-λE | B | 
 |------|---|
 |  C   | D |
```

by explicitly determining for each polynomial entry, its coefficients from its roots and a corresponding gain. 

The keyword arguments `atol1` and `atol2` specify the absolute tolerances for the elements of `A`, `B`, `C`, `D`, and,   respectively, of `E`, and `rtol` specifies the relative tolerances for the nonzero elements of `A`, `B`, `C`, `D` and `E`. The default relative tolerance is `(n+1)*ϵ`, where `n` is the size of the size dimension of `A`, and `ϵ` is the  machine epsilon of the element type of coefficients of `A`. 

The keyword argument `gaintol` specifies the threshold for the magnitude of the nonzero elements of the gain matrix  `C*inv(γE-A)*B+D`, where `γ = val` if `val` is a number or `γ` is a randomly chosen complex value of unit magnitude,  if `val = missing`. Generally, `val` should not be a root of any of entries of `P`.
