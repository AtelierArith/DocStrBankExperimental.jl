```
gir_lrtran(sys; ltran = false, rtran = false, finite = true, infinite = true, contr = true, obs = true, 
         noseig = false, fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ) -> (sysr, Q, Z)
```

This is a special version of the function `gir` to additionally determine the left and right  transformation matrices `Q = [Q1 Q2]` and `Z = [Z1 Z2]`, respectively, such that the matrices `Ar`, `Er`, `Br` and `Cr` of the resulting descriptor system `sysr = (Ar-λEr,Br,Cr,Dr)` are given by `Ar = Q1'*A*Z1`, `Er = Q1'*E*Z1`, `Br = Q1'*B`, `Cr = C*Z1`,  where the number of columns of `Q1` and `Z1` is equal to the order of matrix `Ar`. `Q` and `Z` result orthogonal if `noseig = false`.  `Q = nothing` if `ltran = false` and `Z = nothing` if `rtran = false`.  See [`gir`](@ref) for details on the rest of keyword parameters.
