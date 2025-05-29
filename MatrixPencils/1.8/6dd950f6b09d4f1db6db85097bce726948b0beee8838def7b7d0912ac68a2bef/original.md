```
fiblkdiag(A, E, B, C; fast = true, finite_infinite = false, trinv = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (At, Et, Bt, Ct, Q, Z, ν, blkdims, sep)
```

Reduce the regular matrix pencil `A - λE` to an equivalent form `At - λEt = Q*(A - λE)*Z` using  the transformation matrices `Q` and `Z` such that the transformed matrices `At` and `Et` are in one of the following block diagonal forms:

(1) if `finite_infinite = false`, then

```
               | Ai-λEi |   0     |
    At - λEt = |--------|---------|, 
               |    O   | Af-λEf  |
```

where the `ni x ni` subpencil `Ai-λEi` contains the infinite elementary  divisors and the `nf x nf` subpencil `Af-λEf`, with `Ef` nonsingular and upper triangular, contains the finite eigenvalues of the pencil `A-λE`.

The subpencil `Ai-λEi` is in a staircase form, with `Ai` nonsingular and upper triangular and `Ei` nilpotent and upper triangular.  The `nb`-dimensional vector `ν` contains the dimensions of the diagonal blocks of the staircase form  `Ai-λEi` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[i]-ν[i+1]` for `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `ν[nb+1] = 0`).

The dimensions of the diagonal blocks are returned in `blkdims = (ni, nf)`.   

(2) if `finite_infinite = true`, then

```
               | Af-λEf |   0    |
    At - λEt = |--------|--------|, 
               |   O    | Ai-λEi |
```

where the `nf x nf` subpencil `Af-λEf`, with `Ef` nonsingular and upper triangular,  contains the finite eigenvalues of the pencil `A-λE` and the `ni x ni` subpencil `Ai-λEi`  contains the infinite elementary divisors.

The subpencil `Ai-λEi` is in a staircase form, with `Ai` nonsingular and upper triangular  and `Ei` nilpotent and upper triangular.  The `nb`-dimensional vectors `ν` contains the dimensions of the diagonal blocks of the staircase form `Ai-λEi` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[nb-j+1]-ν[nb-j]` for `j = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `j` (with `ν[0] = 0`).

The dimensions of the diagonal blocks are returned in `blkdims = (nf, ni)`.   

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. 

The reduction is performed using rank decisions based on rank revealing QR-decomdiagpositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

If `withQ = true`, `Q` contains the left transformation matrix, if `trinv = false`, or its inverse, if `trinv = true`.  If `withQ = false`, `Q` is set to `nothing`.    If `withZ = true`, `Z` contains the right transformation matrix, if `trinv = false`, or its inverse, if `trinv = true`.  If `withZ = false`, `Z` is set to `nothing`.   

`Bt = Q*B`, unless `B = missing`, in which case `Bt = missing` is returned, and `Ct = C*Z`,  unless `C = missing`, in which case `Ct = missing` is returned .              

An estimation of the separation of the spectra of `Ai-λEi` and `Af-λEf` is returned in `sep`, where  `0 < sep ≤ 1`.
