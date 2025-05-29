```
expval = expect(dualpsi,psi,H[,Lbound=,Rbound=,order=])
```

evaluate <`dualpsi`|`H`|`psi`> for any number of MPOs `H`; can specifcy left and right boundaries (`Lbound` and `Rbound`); `dualpsi` is conjugated inside of the algorithm; output is an expectation value `expval`

See also: [`overlap`](@ref)
