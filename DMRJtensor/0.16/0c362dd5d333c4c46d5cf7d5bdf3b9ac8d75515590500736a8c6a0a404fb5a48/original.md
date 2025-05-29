```
D,truncerr = moveR(Lpsi,Rpsi[,cutoff=,m=,minm=,condition=])
```

moves `psi`'s orthogonality center right one space, with a maximum bond dimenion `m`, cutoff `cutoff`, minimum bond dimension `minm`; toggle truncation of tensor during movement with `condition`; returns psi[iL],psi[iR],D from the SVD, and the truncation error

See also: [`moveR!`](@ref)
