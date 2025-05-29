```
klf_left(M, N; fast = true, ut = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (F, G, Q, Z, ν, μ, nf, νl, μl)
```

Reduce the matrix pencil `M - λN` to an equivalent form `F - λG = Q'(M - λN)Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `F` and `G` are in the following Kronecker-like form exhibiting the finite and left Kronecker structures:

```
               |  Mri-λNri  |     *      |    *    |
               |------------|------------|---------|
     F - λG =  |    O       |   Mf-λNf   |    *    |
               |------------|------------|---------|
               |    O       |     0      |  Ml-λNl |
```

The full row rank pencil `Mri-λNri` is in a staircase form, and contains the right Kronecker indices  and infinite elementary divisors of the pencil `M-λN`.

The `nf x nf` pencil `Mf-λNf` is regular and contains the finite elementary divisors of `M-λN`.  `Nf` is upper triangular and nonsingular.

The full column rank pencil `Ml-λNl`, in a staircase form, contains the left Kronecker indices of `M-λN` and has the form

```
               | Al-λEl |
     Ml-λNl  = |--------|,
               |   Cl   |
```

where `El` is upper triangular and nonsingular. 

The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mri-λNri` such that `i`-th block has dimensions `ν[i] x μ[i]` and  has full row rank.  The difference `μ[i]-ν[i]` for `i = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size `(i-1) x i`. The difference `ν[i]-μ[i+1]` for `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `μ[nb+1] = 0`). If `ut = true`, the full row rank diagonal blocks of `Mri` are reduced to the form `[0 X]`  with `X` upper triangular and nonsingular and the full column rank supradiagonal blocks of `Nri` are reduced to the form `[Y; 0]` with `Y` upper triangular and nonsingular. 

The `nl`-dimensional vectors `νl` and `μl` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Ml-λNl` such that the `j`-th block has dimensions `νl[j] x μl[j]` and has full column rank.  The difference `νl[nl-j+1]-μl[nl-j+1]` for `j = 1, 2, ..., nl` is the number of elementary Kronecker blocks of size  `j x (j-1)`. If `ut = true`, the full column rank diagonal blocks of `Ml` are reduced to the form `[X; 0]`  with `X` upper triangular and nonsingular and the full row rank supradiagonal blocks of `Nl` are reduced to the form `[0 Y]` with `Y` upper triangular and nonsingular. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  

`Note:` If the pencil `M - λN` has full column rank, then the regular pencil `Mri-λNri` is in a staircase form with square upper triangular diagonal blocks (i.e.,`μ[i] = ν[i]`), and the difference `ν[i+1]-ν[i]` for `i = 1, 2, ..., nb`  is the number of infinite elementary divisors of degree `i` (with `ν[nb+1] = 0`).
