```
klf_rlsplit(M, N; fast = true, finite_infinite = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (F, G, Q, Z, ν, μ, n, m, p)
```

Reduce the matrix pencil `M - λN` to an equivalent form `F - λG = Q'*(M - λN)*Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `F` and `G` are in one of the following Kronecker-like forms:

(1) if `finite_infinite = false`, then

```
               | Mri-λNri |     *      |
      F - λG = |----------|------------|, 
               |    O     | Mfl-λNfl   |
```

where the subpencil `Mri-λNri` contains the right Kronecker structure and infinite elementary  divisors and the subpencil `Mfl-λNfl` contains the finite and left Kronecker structure of the pencil `M-λN`.

The full row rank subpencil `Mri-λNri` is in a staircase form.  The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mri-λNri` such that `i`-th block has dimensions `ν[i] x μ[i]` and  has full row rank.  The difference `μ[i]-ν[i]` for `i = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size `(i-1) x i`. The difference `ν[i]-μ[i+1]` for `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `μ[nb+1] = 0`).

The full column rank subpencil `Mfl-λNfl` is in the form 

```
                 | A-λE | 
      Mfl-λNfl = |------| ,        
                 |  C   |
```

where `E` is an nxn non-singular upper triangular matrix, and `A` and `C` are `nxn`- and `pxn`-dimensional matrices, respectively, and `m = 0`. 

(2) if `finite_infinite = true`, then

```
               | Mrf-λNrf |     *      |
      F - λG = |----------|------------|, 
               |    O     | Mil-λNil   |
```

where the subpencil `Mrf-λNrf` contains the right Kronecker and finite Kronecker structures and  the subpencil `Mil-λNil` contains the left Kronecker structures and infinite elementary  divisors of the pencil `M-λN`. 

The full row rank subpencil `Mrf-λNrf` is in the form 

```
      Mrf-λNrf = | B  | A-λE | ,
```

where `E` is an `nxn` non-singular upper triangular matrix, and `A` and `B` are `nxn`- and `nxm`-dimensional matrices, respectively, and `p = 0`.  

The full column rank sub pencil `Mil-λNil` is in a staircase form.  The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mil-λNil` such that the `i`-th block has dimensions `ν[i] x μ[i]` and has full column rank.  The difference `ν[nb-j+1]-μ[nb-j+1]` for `j = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size  `j x (j-1)`. The difference `μ[nb-j+1]-ν[nb-j]` for `j = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `j` (with `ν[0] = 0`).

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`. 

The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
