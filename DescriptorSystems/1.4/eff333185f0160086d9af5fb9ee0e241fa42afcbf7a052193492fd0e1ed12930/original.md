```
  gprescale(sys; withB = true, withC = true) -> (sysbal, D1, D2)
```

Balance a descriptor system `sys = (A-λE,B,C,D)` by reducing the 1-norm of the matrix 

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

by row and column balancing using diagonal matrices `D1` and `D2` to make the rows and columns of 

```
              diag(D1,I)  * S * diag(D2,I)
```

as close in norm as possible.

The balancing can be performed optionally on the following  particular matrices:   

```
    S = abs(A)+abs(E),             if withB = false and withC = false ,
    S = ( abs(A)+abs(E)  abs(B) ), if withC = false,    
    S = ( abs(A)+abs(E) ),         if withB = false .
        (   abs(C)     )
```

The diagonal elements of the resulting `D1` and `D2` are the nearest integer powers of 2 resulting from the optimal diagonal scaling determined from a modified version of the algorithm of [1].  For a standard system with `E = I`, `D1 = inv(D2)` and `D2` is computed using an extension of the scaling approach implemented in the LAPACK family `*GEBAL.f`. 

This function is merely an interface to the functions `lsbalance!` of the  [MatrixPencils](https://github.com/andreasvarga/MatrixPencils.jl) package. 

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
