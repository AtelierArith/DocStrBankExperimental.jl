```
D,truncerr = moveL(Lpsi,Rpsi[,cutoff=,m=,minm=,condition=])
```

moves `psi`'s orthogonality center left one space, with a maximum bond dimenion `m`, cutoff `cutoff`, minimum bond dimension `minm`; toggle truncation of tensor during movement with `condition`; returns psi[iL],psi[iR],D from the SVD, and the truncation error. Does not modify `Lpsi` and `Rpsi`

See also: [`moveL!`](@ref)
