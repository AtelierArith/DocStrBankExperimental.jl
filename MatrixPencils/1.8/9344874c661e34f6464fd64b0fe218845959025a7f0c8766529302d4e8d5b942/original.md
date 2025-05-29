```
sklf_right(A, E, B, C, D; fast = true, ut = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (F, G, Q, Z, νr, μr, nf, ν, μ)
```

Reduce the structured matrix pencil `M - λN` 

```
           | A-λE | B | 
  M - λN = |------|---|
           |  C   | D |
```

to an equivalent form `F - λG = Q'*(M - λN)*Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `F` and `G` are in the following Kronecker-like form exhibiting the right and finite Kronecker structures:

```
            |  Mr-λNr    |     *      |    *     |
            |------------|------------|----------|
  F - λG =  |    O       |   Mf-λNf   |    *     |
            |------------|------------|----------|
            |    O       |     0      | Mil-λNil |
```

The full row rank pencil `Mr-λNr`, in a staircase form, contains the right Kronecker indices of `M-λN` and has the form

```
     Mr-λNr  = | Br | Ar-λEr |,
```

where `Er` is upper triangular and nonsingular.  The `nr`-dimensional vectors `νr` and `μr` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mr-λNr` such that `i`-th block has dimensions `νr[i] x μr[i]` and  has full row rank. The difference `μr[i]-νr[i]` for `i = 1, 2, ..., nr` is the number of elementary Kronecker blocks of size `(i-1) x i`. If `ut = true`, the full row rank diagonal blocks of `Mr` are reduced to the form `[0 X]`  with `X` upper triangular and nonsingular and the full column rank supradiagonal blocks of `Nr` are reduced to the form `[Y; 0]` with `Y` upper triangular and nonsingular. 

The `nf x nf` pencil `Mf-λNf` is regular and contains the finite elementary divisors of `M-λN`.  Nf is upper triangular and nonsingular.

The full column rank pencil `Mil-λNil` is in a staircase form, and contains the  left Kronecker indices  and infinite elementary divisors of the pencil `M-λN`.  The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mil-λNil` such that the `i`-th block has dimensions `ν[i] x μ[i]` and has full column rank.  The difference `ν[nb-j+1]-μ[nb-j+1]` for `j = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size  `j x (j-1)`. The difference `μ[nb-j+1]-ν[nb-j]` for `j = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `j` (with `ν[0] = 0`). If `ut = true`, the full column rank diagonal blocks of `Mil` are reduced to the form `[X; 0]`  with `X` upper triangular and nonsingular and the full row rank supradiagonal blocks of `Nil` are reduced to the form `[0 Y]` with `Y` upper triangular and nonsingular. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.   

`Note:` If the pencil `M - λN` has full row rank, then the regular pencil `Mil-λNil` is in a staircase form with square upper triangular diagonal blocks (i.e.,`μ[j] = ν[j]`), and the difference `ν[nb-j+1]-ν[nb-j]` for  `j = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `j` (with `ν[0] = 0`).
