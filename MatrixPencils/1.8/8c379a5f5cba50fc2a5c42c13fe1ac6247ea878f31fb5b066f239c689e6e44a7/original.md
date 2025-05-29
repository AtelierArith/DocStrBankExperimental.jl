```
qs = lsbalqual(A, B, C; SysMat = false)
```

Compute the 1-norm based scaling quality of a standard system triple `(A,B,C)`.

If `SysMat = false`, the resulting `qs` is computed as 

```
    qs = max(qS(A),qS(B),qS(C)) ,
```

where `qS(⋅)` is the scaling quality measure defined in Definition 5.5 of [1] for  nonnegative matrices. This definition has been extended to also cover matrices with zero rows or columns.  

If `SysMat = true`, the resulting `qs` is computed as 

```
    qs = qS(S) ,
```

where `S` is the system matrix defined as        

```
         S =  ( A  B )
              ( C  0 )
```

A large value of `qs` indicates a possible poorly scaled state-space model.   

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
