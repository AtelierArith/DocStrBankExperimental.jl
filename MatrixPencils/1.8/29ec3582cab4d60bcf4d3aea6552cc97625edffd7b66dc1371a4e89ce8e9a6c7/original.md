```
 lsbalance!(A, E, B, C; withB = true, withC = true, pow2, maxiter = 100, tol = 1) -> (D1,D2)
```

Reduce the 1-norm of the matrix 

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

corresponding to a descriptor system triple `(A-λE,B,C)` by row and column balancing.  This involves diagonal similarity transformations `D1*(A-λE)*D2` applied iteratively to `abs(A)+abs(E)` to make the rows and columns of 

```
              diag(D1,I)  * S * diag(D2,I)
```

as close in norm as possible.

The balancing can be performed optionally on the following  particular system matrices:   

```
    S = abs(A)+abs(E), if withB = false and withC = false ,
    S = ( abs(A)+abs(E)  abs(B) ), if withC = false,     or    
    S = ( abs(A)+abs(E) ), if withB = false .
        (   abs(C)     )
```

The keyword argument `maxiter = k` specifies the maximum number of iterations `k`  allowed in the balancing algorithm. 

The keyword argument `tol = τ`, with `τ ≤ 1`,  specifies the tolerance used in the stopping criterion.   

If the keyword argument `pow2 = true` is specified, then the components of the resulting  optimal `D1` and `D2` are replaced by their nearest integer powers of 2, in which case the  scaling of matrices is done exactly in floating point arithmetic.  If `pow2 = false`, the optimal values `D1` and `D2` are returned.

*Note:* This function is an extension of the MATLAB function `rowcolsums.m` of [1]. 

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
