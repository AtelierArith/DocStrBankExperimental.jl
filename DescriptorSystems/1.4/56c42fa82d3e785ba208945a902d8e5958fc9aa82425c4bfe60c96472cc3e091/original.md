```
sysdual = gdual(sys, rev = false) 
sysdual = transpose(sys, rev = false)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`,  the descriptor system realization of its dual system  `sysdual = (Ad-λEd,Bd,Cd,Dd)`, where `Ad = transpose(A)`, `Ed = transpose(E)`, `Bd = transpose(C)`,  `Cd = transpose(B)` and `Dd = transpose(D)`,  such that the transfer function matrix `Gdual(λ)` of `sysdual` is the transpose of `G(λ)`  (i.e., `Gdual(λ) = transpose(G(λ))`). 

If `rev = true`, the tranposition is combined with the reverse permutation of the state variables, such that `sysdual = (P*Ad*P-λP*Ed*P,P*Bd,Cd*P,Dd)`, where `P` is the permutation matrix with ones down the second diagonal. 
