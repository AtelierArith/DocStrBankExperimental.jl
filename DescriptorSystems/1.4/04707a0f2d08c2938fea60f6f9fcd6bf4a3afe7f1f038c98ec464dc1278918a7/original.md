```
qs = gbalqual(sys; SysMat = false)
```

Compute the 1-norm based scaling quality of the matrices of the descriptor system `sys = (A-λE,B,C)`.

If `SysMat = false`, the resulting `qs` is computed as 

```
    qs = max(qS(A),qS(E),qS(B),qS(C)) ,
```

where `qS(⋅)` is the scaling quality measure defined in Definition 5.5 of [1] for  nonnegative matrices, extended to also cover matrices with zero rows or columns.  

If `SysMat = true`, the resulting `qs` is computed as 

```
    qs = qS(S) ,
```

where `S` is the system matrix defined as        

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

A large value of `qs` indicates a possibly poorly scaled state-space model.  For a standard system with `E = I`, the above formulas are used assuming `E = 0`.  

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
