```
sfisplit(A, E, B, C; fast = true, finite_infinite = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (At, Et, Bt, Ct, Q, Z, ν, blkdims)
```

Reduce the regular matrix pencil `A - λE` to an equivalent form `At - λEt = Q'*(A - λE)*Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `At` and `Et` are in one of the following block upper-triangular forms:

(1) if `finite_infinite = true`, then

```
               | Ai1    *        *     |
    At - λEt = | O    Af-λEf     *     |
               | O      0     Ai2-λEi2 |
```

where the `ni1 x ni1` upper triangular nonsingular matrix `Ai1` and the `ni2 x ni2` subpencil `Ai2-λEi2` contain the infinite elementary  divisors and the `nf x nf` subpencil `Af-λEf`, with `Ef` nonsingular and upper triangular, contains the finite eigenvalues of the pencil `A-λE`.

The subpencil `Ai2-λEi2` is in a staircase form, with `Ai2` nonsingular and upper triangular and `Ei2` nilpotent and upper triangular.  The `nb`-dimensional vector `ν` contains the dimensions of the diagonal blocks of the staircase form  `Ai2-λEi2` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[nb-j+2]-ν[nb-j+1]` for `j = 1, 2, ..., nb+1` is the number of infinite elementary  divisors of degree `j` (with `ν[0] := 0` and `ν[nb+1] := ni1`).

The dimensions of the diagonal blocks are returned in `blkdims = (ni1, nf, ni2)`.   

(2) if `finite_infinite = false`, then

```
               | Ai1-λEi1    *      *  |
    At - λEt = | O         Af-λEf   *  |
               | O           0     Ai2 |
```

where the `ni1 x ni1` subpencil `Ai1-λEi1` and the upper triangular nonsingular matrix `Ai2` contain the infinite elementary  divisors and the `nf x nf` subpencil `Af-λEf`, with `Ef` nonsingular and upper triangular, contains the finite eigenvalues of the pencil `A-λE`.

The subpencil `Ai1-λEi1` is in a staircase form, with `Ai1` nonsingular and upper triangular and `Ei1` nilpotent and upper triangular.  The `nb`-dimensional vectors `ν` contains the dimensions of the diagonal blocks of the staircase form `Ai1-λEi1` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[i]-ν[i+1]` for `i = 0, 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `ν[nb+1] = 0` and `ν[0] = ni2`).

The dimensions of the diagonal blocks are returned in `blkdims = (ni1, nf, ni2)`.   

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. 

The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  

`Bt = Q'*B`, unless `B = missing`, in which case `Bt = missing` is returned, and `Ct = C*Z`,  unless `C = missing`, in which case `Ct = missing` is returned .              
