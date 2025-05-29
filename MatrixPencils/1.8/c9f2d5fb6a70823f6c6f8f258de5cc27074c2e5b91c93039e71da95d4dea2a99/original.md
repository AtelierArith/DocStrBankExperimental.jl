```
klf_rightinf(M, N; fast = true, ut = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) 
            -> (F, G, Q, Z, νr, μr, νi, n, p)
```

Reduce the matrix pencil `M - λN` to an equivalent form `F - λG = Q'(M - λN)Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `F` and `G` are in the following Kronecker-like form exhibiting the infinite and left Kronecker structures:

```
               |  Mr-λNr  |     *      |    *     |
               |----------|------------|----------|
     F - λG =  |    O     |   Mi-λNi   |    *     |
               |----------|------------|----------|
               |    O     |     0      | Mfl-λNfl |
```

The full row rank pencil `Mr-λNr` is in a staircase form, contains the right Kronecker indices  of the pencil `M-λN`and has the form

```
     Mr-λNr  = | Br | Ar-λEr |,
```

where `Er` is upper triangular and nonsingular.  The `nr`-dimensional vectors `νr` and `μr` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mr-λNr` such that the `i`-th block has dimensions `νr[i] x μr[i]` and  has full row rank. The difference `μr[i]-νr[i]` for `i = 1, 2, ..., nr` is the number of elementary Kronecker  blocks of size `(i-1) x i`.  If `ut = true`, the full row rank diagonal blocks of `Mr` are reduced to the form `[0 X]`  with `X` upper triangular and nonsingular and the full column rank supradiagonal blocks of `Nr` are reduced to the form `[Y; 0]` with `Y` upper triangular and nonsingular. 

The regular pencil `Mi-λNi` is in a staircase form, contains the infinite elementary divisors of `M-λN`  with `Mi` upper triangular if `ut = true` and nonsingular, and `Ni` is upper triangular and nilpotent.  The `ni`-dimensional vector `νi` contains the dimensions of the  square diagonal blocks of the staircase form  `Mi-λNi` such that the `i`-th block has dimensions `νi[i] x νi[i]`.  The difference `νi[ni-i+1]-νi[ni-i]` for `i = 1, 2, ..., ni` is the number of infinite elementary divisors of degree `i` (with `νi[0] = 0`).

The full column rank pencil `Mfl-λNfl` contains the left Kronecker   and finite Kronecker structures of the pencil `M-λN` and is in the form 

```
                 | A-λE | 
      Mfl-λNfl = |------| ,        
                 |  C   |
```

where `E` is an nxn non-singular upper triangular matrix, and `A` and `C` are `nxn`- and `pxn`-dimensional matrices, respectively.                      

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
