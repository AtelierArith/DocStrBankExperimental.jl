```
lps2rm(A, E, B, F, C, G, D, H; fast = true, atol1 = 0, atol2 = 0, gaintol = 0, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val) -> (NUM, DEN)
```

Build the rational matrix `R(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH := NUM(λ) ./ DEN(λ)` corresponding to its structured linearization 

```
        | A-λE | B-λF | 
 S(λ) = |------|------|
        | C-λG | D-λH |
```

by explicitly determining for each rational entry of `R(λ)`, its numerator coefficients from its finite zeros and gain, and  its denominator coefficients from its finite poles. An extension of the approach of [1] is employed, relying on the procedures of [2] to compute strongly irreducible linearizations.

The keyword arguments `atol1` and `atol2` specify the absolute tolerances for the elements of `A`, `B`, `C`, `D`, and of   `E`, `F`, `G`, `H`, respectively,  and `rtol` specifies the relative tolerances for the nonzero elements of  `A`, `B`, `C`, `D`, `E`, F`,`G`,`H`.  The default relative tolerance is`(n+2)*ϵ`, where`n`is the size of the size dimension of`A`, and`ϵ`is the  machine epsilon of the element type of coefficients of`A`. 

The keyword argument `gaintol` specifies the threshold for the magnitude of the nonzero elements of the gain matrix  `C*inv(γE-A)*B+D`, where `γ = val` if `val` is a number or `γ` is a randomly chosen complex value of unit magnitude,  if `val = missing`. Generally, `val` should not be a root of any of entries of `P`. 

[1] A. Varga Computation of transfer function matrices of generalized state-space models.      Int. J. Control, 50:2543–2561, 1989.

[2] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions,  in "Realization and Model Reduction of Dynamical Systems, A Festschrift to honor the 70th birthday of Thanos Antoulas",  Eds. C. Beattie, P. Benner, M. Embree, S. Gugercin and S. Lefteriu, Springer-Verlag, 2020.  [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)
