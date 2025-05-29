```
fihess(A, E; fast = true, finite_infinite = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (At, Et, Q, Z, ν, blkdims)
```

Reduce the regular matrix pencil `A - λE` to an equivalent form `At - λEt = Q'*(A - λE)*Z` using  orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `At` and `Et` are in one of the following block upper-triangular forms:

(1) if `finite_infinite = false`, then

```
               | Ai-λEi |   *     |
    At - λEt = |--------|---------|, 
               |    O   | Af-λEf  |
```

where the `ni x ni` subpencil `Ai-λEi` contains the infinite elementary divisors and  the `nf x nf` subpencil `Af-λEf` contains the finite eigenvalues of the pencil `A-λE`.

The subpencil `Ai-λEi` is in a staircase form, with `Ai` nonsingular and upper triangular and `Ei` nilpotent and upper triangular.  The `nb`-dimensional vector `ν` contains the dimensions of the diagonal blocks of the staircase form  `Ai-λEi` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[i]-ν[i+1]` for `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `ν[nb+1] = 0`).

The subpencil `Af-λEf` is with `Af` in an upper Hessenberg form and `Ef` nonsingular and upper triangular. 

The dimensions of the diagonal blocks are returned in `blkdims = (ni, nf)`.   

(2) if `finite_infinite = true`, then

```
               | Af-λEf |   *    |
    At - λEt = |--------|--------|, 
               |   O    | Ai-λEi |
```

where the `nf x nf` subpencil `Af-λEf`, with `Ef` nonsingular and upper triangular,  contains the finite eigenvalues of the pencil `A-λE` and the `ni x ni` subpencil `Ai-λEi`  contains the infinite elementary divisors.

The subpencil `Af-λEf` is with `Af` in an upper Hessenberg form and `Ef` nonsingular and upper triangular.  

The subpencil `Ai-λEi` is in a staircase form, with `Ai` nonsingular and upper triangular  and `Ei` nilpotent and upper triangular.  The `nb`-dimensional vectors `ν` contains the dimensions of the diagonal blocks of the staircase form `Ai-λEi` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[nb-j+1]-ν[nb-j]` for `j = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `j` (with `ν[0] = 0`).

The dimensions of the diagonal blocks are returned in `blkdims = (nf, ni)`.   

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. 

The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
