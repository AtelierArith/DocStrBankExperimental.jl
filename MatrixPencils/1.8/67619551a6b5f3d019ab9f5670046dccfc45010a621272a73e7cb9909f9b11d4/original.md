```
klf_left!(M, N; fast = true, roff = 0, coff = 0, rtrail = 0, ctrail = 0, atol = 0, rtol, withQ = true, withZ = true) -> (Q, Z, ν, μ, nf, νl, μl, tol)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
          [   *         *        *  ] roff
 M - λN = [   0      M22-λN22    *  ] m
          [   0         0        *  ] rtrail
            coff        n     ctrail
```

to an equivalent form `F - λG = Q1'*(M - λN)*Z1` using orthogonal or unitary transformation matrices `Q1` and `Z1`  such that the subpencil `M22 - λN22`  is transformed into the following Kronecker-like form exhibiting  its finite and left Kronecker structures

```
               |  Mri-λNri  |     *      |    *    |
               |------------|------------|---------|
 F22 - λG22 =  |    O       |   Mf-λNf   |    *    |
               |------------|------------|---------|
               |    O       |     0      |  Ml-λNl |
```

`F` and `G` are returned in `M` and `N`, respectively.                

The full row rank pencil `Mri-λNri` is in a staircase form, and contains the right Kronecker indices  and infinite elementary divisors of the subpencil `M22 - λN22`.  The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mri-λNri` such that `i`-th block has dimensions `ν[i] x μ[i]` and  has full row rank.  The difference `μ[i]-ν[i]` for `i = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size `(i-1) x i`. The difference `ν[i]-μ[i+1]` for `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `μ[nb+1] = 0`).

The `nf x nf` pencil `Mf-λNf` is regular and contains the finite elementary divisors of `M-λN`.  `Nf` is upper triangular and nonsingular.

The full column rank pencil `Ml-λNl`, in a staircase form, contains the left Kronecker indices of `M-λN` and has the form

```
               | Al-λEl |
     Ml-λNl  = |--------|,
               |   Cl   |
```

where `El` is upper triangular and nonsingular.  The `nl`-dimensional vectors `νl` and `μl` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Ml-λNl` such that `j`-th block has dimensions `νl[nl-j+1] x μl[nl-j+1]` and has full column rank.  The difference `νl[nl-j+1]-μl[nl-j+1]` for `j = 1, 2, ..., nl` is the number of elementary Kronecker blocks of size  `j x (j-1)`.

The keyword arguments `atol` and `rtol`, specify the absolute and relative tolerances for the  nonzero elements of `M`, respectively. The internally employed absolute tolerance  for the  nonzero elements of `M` is returned in `tol`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` (i.e., `Q <- Q*Q1`)  if `withQ = true`. Otherwise, `Q` is not modified.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` (i.e., `Z <- Z*Z1`)  if `withZ = true`. Otherwise, `Z` is not modified.   

`Note:` If the pencil `M22 - λN22` has full column rank, then the regular pencil `Mri-λNri` is in a staircase form with square diagonal blocks (i.e.,`μ[i] = ν[i]`), and the difference `ν[i]-ν[i+1]` for `i = 1, 2, ..., nb`  is the number of infinite elementary divisors of degree `i` (with `ν[nb+1] = 0`).
