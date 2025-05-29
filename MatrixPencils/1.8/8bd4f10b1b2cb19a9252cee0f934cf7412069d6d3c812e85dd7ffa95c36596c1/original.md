```
 lsbalance!(A, B, C; withB = true, withC = true, maxred = 16) -> D
```

Reduce the 1-norm of a system matrix 

```
         S =  ( A  B )
              ( C  0 )
```

corresponding to a standard system triple `(A,B,C)` by balancing.  This involves a diagonal similarity transformation `inv(D)*A*D`  to make the rows and columns of 

```
              diag(inv(D),I) * S * diag(D,I)
```

as close in norm as possible.

The balancing can be optionally performed on the following  particular system matrices:   

```
    S = A, if withB = false and withC = false ,
    S = ( A  B ), if withC = false,     or    
    S = ( A ), if withB = false .
        ( C )
```

The keyword argument `maxred = s` specifies the maximum allowed reduction in the 1-norm of `S` (in an iteration) if zero rows or columns are present.  `s` must be a positive power of `2`, otherwise  `s` is rounded to the nearest power of 2.   

*Note:* This function is a translation of the SLICOT routine `TB01ID.f`, which  represents an extensiom of the LAPACK family `*GEBAL.f` and also includes   the fix proposed in [1]. 

[1]  R.James, J.Langou and B.Lowery. "On matrix balancing and eigenvector computation."      ArXiv, 2014, http://arxiv.org/abs/1401.5766
