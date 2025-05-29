```
klf_left_refine!(ν, μ, M, N, tol; fast = true, ut = false, roff = 0, coff = 0, rtrail = 0, ctrail = 0, withQ = true, withZ = true) -> (νi, νl, μl)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
         [   *         *        *  ] roff
M - λN = [   0      Mil-λNil    *  ] mli
         [   0         0        *  ] rtrail
           coff      nli     ctrail
```

to an equivalent form `F - λG = Q1'*(M - λN)*Z1` using orthogonal or unitary transformation matrices `Q1` and `Z1`  such that the full column rank subpencil `Mil-λNil` is transformed into the  following Kronecker-like form  exhibiting its infinite and left Kronecker structures:

```
              |  Mi-λNi    |     *      |
 Fil - λGil = |------------|------------|
              |    O       |   Ml-λNl   |
```

The full column rank pencil `Mil-λNil` is in a staircase form and the `nb`-dimensional vectors `ν` and `μ`  contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mil-λNil` such that  the `i`-th block has dimensions `ν[i] x μ[i]` and has full column rank. The matrix Mil has full column rank and  the leading `μ[1]+...+μ[nb-1]` columns of `Nil` form a full row rank submatrix. 

The regular pencil `Mi-λNi` is in a staircase form, contains the infinite elementary divisors of `Mil-λNil`,   `Mi` is upper triangular if `ut = true` and nonsingular and `Ni` is upper triangular and nilpotent. The `nbi`-dimensional vector `νi` contains the dimensions of the  square diagonal blocks of the staircase form  `Mi-λNi` such that the `i`-th block has dimensions `νi[i] x νi[i]`.  The difference `νi[i]-νi[i-1] = ν[nbi-i+1]-μ[nbi-i+1]` for `i = 1, 2, ..., nbi` is the number of infinite elementary  divisors of degree `i` (with `νi[0] = 0` and `μ[nbi+1] = 0`).

The full column rank pencil `Mil-λNil` is in a staircase form, and contains the  left Kronecker indices  and infinite elementary divisors of the subpencil `M22 - λN22`.  The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mil-λNil` such that the `i`-th block has dimensions `ν[nb-i+1] x μ[nb-i+1]` and has full column rank.  The difference `ν[nb-i+1]-μ[nb-i+1]` for `i = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size  `i x (i-1)`. The difference `μ[nb-i+1]-ν[nb-i]` for `i = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `i` (with `ν[0] = 0`).

The full column rank pencil `Ml-λNl`, in a staircase form, contains the left Kronecker indices of `M-λN` and has the form

```
           | Al-λEl |
 Ml-λNl  = |--------|,
           |   Cl   |
```

where `El` is upper triangular and nonsingular.  The `nl`-dimensional vectors `νl` and `μl` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Ml-λNl` such that the `j`-th block has dimensions `νl[j] x μl[j]` and has full column rank.  The difference `νl[nl-j+1]-μl[nl-j+1] = ν[nl-j+1]-μ[nl-j+1]` for `j = 1, 2, ..., nl` is the number of elementary  Kronecker blocks of size `j x (j-1)`. If `ut = true`, the full column rank diagonal blocks of `Ml` are reduced to the form `[Y; 0]`  with `Y` upper triangular and nonsingular and the full row rank supradiagonal blocks of `Nl` are reduced to the form `[0 Y]` with `Y` upper triangular and nonsingular. 

`F` and `G` are returned in `M` and `N`, respectively.  

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` (i.e., `Q <- Q*Q1`)  if `withQ = true`. Otherwise, `Q` is not modified.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` (i.e., `Z <- Z*Z1`)  if `withZ = true`. Otherwise, `Z` is not modified.   
