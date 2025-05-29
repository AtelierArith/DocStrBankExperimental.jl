```
qs = pbalqual(M, N)
```

Compute the 1-norm based scaling quality of a matrix pencil `M-λN`.

The resulting `qs` is computed as 

```
    qs = qS(abs(M)+abs(N)) ,
```

where `qS(⋅)` is the scaling quality measure defined in Definition 5.5 of [1] for  nonnegative matrices. This definition has been extended to also cover matrices with zero rows or columns. If `N = I`, `qs = qs(M)` is computed. 

A large value of `qs` indicates a possibly poorly scaled matrix pencil.   

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
