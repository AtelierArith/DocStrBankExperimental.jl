```
rho = correlationmatrix(dualpsi,psi,Cc,Ca[,F,silent=])
```

Compute the correlation funciton (example, <`dualpsi`|`Cc`*i . `Ca`*j|`psi`>) on all sites; can also specify a trail `F` for Fermion strings; `silent` toggles output of every line; outputs matrix `rho`

# Note:

  * More efficient than using `mpoterm`s or `correlation`
  * Use `mpoterm` and `applyMPO` for higher order correlation functions or write a new function
