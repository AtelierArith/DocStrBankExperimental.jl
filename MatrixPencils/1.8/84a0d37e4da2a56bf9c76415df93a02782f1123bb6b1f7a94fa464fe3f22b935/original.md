```
klf_right!(M, N; fast = true, roff = 0, coff = 0, rtrail = 0, ctrail = 0, atol = 0, rtol, withQ = true, withZ = true) -> (Q, Z, νr, μr, nf, ν, μ, tol)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
          [   *         *        *  ] roff
 M - λN = [   0      M22-λN22    *  ] m
          [   0         0        *  ] rtrail
            coff        n     ctrail
```

to an equivalent form `F - λG = Q1'*(M - λN)*Z1` using orthogonal or unitary transformation matrices `Q1` and `Z1`  such that the subpencil `M22 - λN22` is transformed into the following Kronecker-like form exhibiting  its right and finite Kronecker structures:

```
               |  Mr-λNr    |     *      |    *     |
               |------------|------------|----------|
 F22 - λG22 =  |    O       |   Mf-λNf   |    *     |
               |------------|------------|----------|
               |    O       |     0      | Mil-λNil |
```

`F` and `G` are returned in `M` and `N`, respectively.                

The full row rank pencil `Mr-λNr`, in a staircase form, contains the right Kronecker indices of  the subpencil `M22 - λN22` and has the form

```
     Mr-λNr  = | Br | Ar-λEr |,
```

where `Er` is upper triangular and nonsingular.  The `nr`-dimensional vectors `νr` and `μr` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mr-λNr` such that `i`-th block has dimensions `νr[i] x μr[i]` and  has full row rank. The difference `μr[i]-νr[i]` for `i = 1, 2, ..., nr` is the number of elementary Kronecker blocks of size `(i-1) x i`.

The `nf x nf` pencil `Mf-λNf` is regular and contains the finite elementary divisors of the subpencil `M22 - λN22`.  `Nf` is upper triangular and nonsingular.

The full column rank pencil `Mil-λNil` is in a staircase form, and contains the  left Kronecker indices  and infinite elementary divisors of the subpencil `M22 - λN22`.  The `nb`-dimensional vectors `ν` and `μ` contain the row and, respectively, column dimensions of the blocks of the staircase form  `Mil-λNil` such that the `i`-th block has dimensions `ν[nb-i+1] x μ[nb-i+1]` and has full column rank.  The difference `ν[nb-i+1]-μ[nb-i+1]` for `i = 1, 2, ..., nb` is the number of elementary Kronecker blocks of size  `i x (i-1)`. The difference `μ[nb-i+1]-ν[nb-i]` for `i = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `i` (with `ν[0] = 0`).

The keyword arguments `atol` and `rtol`, specify the absolute and relative tolerances for the  nonzero elements of `M`, respectively. The internally employed absolute tolerance  for the  nonzero elements of `M` is returned in `tol`.  The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` (i.e., `Q <- Q*Q1`)  if `withQ = true`. Otherwise, `Q` is not modified.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` (i.e., `Z <- Z*Z1`)  if `withZ = true`. Otherwise, `Z` is not modified.   

`Note:` If the subpencil `M22 - λN22` has full row rank, then the regular pencil `Mil-λNil` is in a staircase form with square upper triangular diagonal blocks (i.e.,`μ[i] = ν[i]`), and the difference `ν[nb-i+1]-ν[nb-i]` for  `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i` (with `ν[0] = 0`).
