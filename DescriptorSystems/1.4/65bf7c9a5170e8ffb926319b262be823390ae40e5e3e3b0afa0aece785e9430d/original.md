```
sysldiv = ldiv(sys1, sys2; atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ, checkinv = true)
sysldiv = sys1 \ sys2
```

Compute for the descriptor systems `sys1 = (A1-λE1,B1,C1,D1)` with the transfer function matrix `G1(λ)` and  `sys2 = (A2-λE2,B2,C2,D2)` with the transfer function matrix `G2(λ)`, a descriptor realization  `sysldiv = (Ai-λEi,Bi,Ci,Di)` of `sysldiv = inv(sys1)*sys2`, whose transfer-function matrix `Gli(λ)` represents the result of the left division `Gli(λ) = inv(G1(λ))*G2(λ)`.  The realization of `sysldiv` is determined using inversion-free formulas and the invertibility condition for `sys1` is checked,  unless `checkinv = false`.

The keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A1`, `B1`, `C1`, `D1`, `A2`, `B2`, `C2`, `D2`,  the absolute tolerance for the nonzero elements of `E1` and `E2`,  and the relative tolerance for the nonzero elements of `A1`, `B1`, `C1`, `D1`, `A2`, `B2`, `C2`, `D2`, `E1` and `E2`.   The default relative tolerance is `n*ϵ`, where `n` is the maximum of orders of the square matrices `A1` and `A2`, and  `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
