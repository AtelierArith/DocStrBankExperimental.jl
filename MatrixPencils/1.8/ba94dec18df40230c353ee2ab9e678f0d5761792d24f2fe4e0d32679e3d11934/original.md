```
 klf_right_refine!(ν, μ, M, N, tol; fast = true, ut = false, roff = 0, coff = 0, rtrail = 0, ctrail = 0, withQ = true, withZ = true) -> (νr, μr, νi)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
         [   *         *        *  ] roff
M - λN = [   0      Mri-λNri    *  ] mri
         [   0         0        *  ] rtrail
           coff      nri     ctrail
```

to an equivalent form `F - λG = Q1'*(M - λN)*Z1` using orthogonal or unitary transformation matrices `Q1` and `Z1`  such that the full row rank subpencil `Mri-λNri`is transformed into the  following Kronecker-like form  exhibiting its right and infinite Kronecker structures:

```
              |  Mr-λNr    |     *      |
 Fri - λGri = |------------|------------|
              |    O       |   Mi-λNi   |
```

The full row rank pencil `Mri-λNri` is in a staircase form and the `nb`-dimensional vectors `ν` and `μ`  contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mri-λNri` such that  the `i`-th block has dimensions `ν[i] x μ[i]` and has full row rank. The matrix Mri has full row rank and  the trailing `μ[2]+...+μ[nb]` columns of `Nri` form a full column rank submatrix. 

The full row rank pencil `Mr-λNr` is in a staircase form, contains the right Kronecker indices  of the pencil `M-λN`and has the form

```
  Mr-λNr  = | Br | Ar-λEr |,
```

where `Er` is upper triangular and nonsingular.  The `nr`-dimensional vectors `νr` and `μr` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mr-λNr` such that the `i`-th block has dimensions `νr[i] x μr[i]` and  has full row rank. The difference `μr[i]-νr[i] = μ[i]-ν[i]` for `i = 1, 2, ..., nr` is the number of  elementary Kronecker blocks of size `(i-1) x i`. If `ut = true`, the full row rank diagonal blocks of `Mr` are reduced to the form `[0 X]`  with `X` upper triangular and nonsingular and the full column rank supradiagonal blocks of `Nr` are reduced to the form `[Y; 0]` with `Y` upper triangular and nonsingular. 

The regular pencil `Mi-λNi`is in a staircase form, contains the infinite elementary divisors of `Mri-λNri`,  `Mi` is upper triangular if `ut = true` and nonsingular and `Ni` is upper triangular and nilpotent. The `ni`-dimensional vector `νi` contains the dimensions of the  square diagonal blocks of the staircase form  `Mi-λNi` such that the `i`-th block has dimensions `νi[i] x νi[i]`.  The difference `νi[ni-i+1]-νi[ni-i] = ν[i]-μ[i+1]` for `i = 1, 2, ..., ni` is the number of infinite elementary  divisors of degree `i` (with `νi[0] = 0` and `μ[nb+1] = 0`).

`F` and `G` are returned in `M` and `N`, respectively.  

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` (i.e., `Q <- Q*Q1`)  if `withQ = true`. Otherwise, `Q` is not modified.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` (i.e., `Z <- Z*Z1`)  if `withZ = true`. Otherwise, `Z` is not modified.   
