```
klf_leftinf(M, N; fast = true, ut = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) 
            -> (F, G, Q, Z, n, m, νi, νl, μl)
```

Reduce the matrix pencil `M - λN` to an equivalent form `F - λG = Q'(M - λN)Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `F` and `G` are in the following Kronecker-like form exhibiting the infinite and left Kronecker structures:

```
               |  Mrf-λNrf  |     *      |    *    |
               |------------|------------|---------|
     F - λG =  |    O       |   Mi-λNi   |    *    |
               |------------|------------|---------|
               |    O       |     0      |  Ml-λNl |
```

The full row rank pencil `Mrf-λNrf` contains the right Kronecker   and finite Kronecker structures of the pencil `M-λN` and is in the standard form 

```
      Mrf-λNrf = | B  | A-λE | ,
```

where `E` is an `nxn` non-singular upper triangular matrix, and `A` and `B` are `nxn`- and `nxm`-dimensional matrices, respectively.                      

The regular pencil `Mi-λNi` is in a staircase form, contains the infinite elementary divisors of `M-λN`  with `Mi` upper triangular if `ut = true` and nonsingular, and `Ni` is upper triangular and nilpotent.  The `ni`-dimensional vector `νi` contains the dimensions of the  square diagonal blocks of the staircase form  `Mi-λNi` such that the `i`-th block has dimensions `νi[i] x νi[i]`.  The difference `νi[i]-νi[i-1] = ν[ni-i+1]-μ[ni-i+1]` for `i = 1, 2, ..., ni` is the number of infinite elementary  divisors of degree `i` (with `νi[0] = 0` and `μ[nb+1] = 0`).

The full column rank pencil `Ml-λNl`, in a staircase form, contains the left Kronecker indices of `M-λN` and has the form

```
               | Al-λEl |
     Ml-λNl  = |--------|,
               |   Cl   |
```

where `El` is upper triangular and nonsingular. 

The `nl`-dimensional vectors `νl` and `μl` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Ml-λNl` such that the `j`-th block has dimensions `νl[j] x μl[j]` and has full column rank.  The difference `νl[nl-j+1]-μl[nl-j+1]` for `j = 1, 2, ..., nl` is the number of elementary Kronecker blocks of size  `j x (j-1)`. If `ut = true`, the full column rank diagonal blocks of `Ml` are reduced to the form `[X; 0]`  with `X` upper triangular and nonsingular and the full row rank supradiagonal blocks of `Nl` are reduced to the form `[0 Y]` with `Y` upper triangular and nonsingular. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
