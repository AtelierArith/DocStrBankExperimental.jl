```
fischursep(A, E; smarg, disc = false, fast = true, finite_infinite = false, stable_unstable = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (At, Et, Q, Z, ν, blkdims)
```

Reduce the regular matrix pencil `A - λE` to an equivalent block upper triangular form `At - λEt = Q'*(A - λE)*Z`  using orthogonal or unitary transformation matrices `Q` and `Z` such that the transformed matrices `At` and `Et`  have separated infinite, stable and unstable eigenvalues with respect to a stability domain `Cs` defined by the stability margin parameter `smarg` and  the stability type parameter `disc`. If `disc = false`, `Cs` is the set of complex numbers with real parts less than `smarg`,  while if `disc = true`, `Cs` is the set of complex numbers with moduli less than `smarg` (i.e., the interior of a disc  of radius `smarg` centered in the origin). If `smarg = missing`, the default value used is `smarg = 0`, if  `disc = false`, and `smarg = 1`, if `disc = true`.

The pencil `At - λEt` results in one of the following block upper-triangular forms:

(1) if `finite_infinite = false`, then

```
               | Ai-λEi   *      *    |
    At - λEt = |    O   A1-λE1   *    |
               |    0     0    A2-λE2 |
```

where the `ni x ni` subpencil `Ai-λEi` contains the infinite elementary divisors,  the `n1 x n1` subpencil `A1-λE1` is with the pair `(A1,E1)` in a generalized Schur form, and the  `n2 x n2` subpencil `A2-λE2` is with the pair `(A2,E2)` in a generalized Schur form.  The pencil `A1-λE1` has unstable finite eigenvalues and `A2-λE2` has stable finite eigenvalues if `stable_unstable = false`, while `A1-λE1` has stable finite eigenvalues and `A2-λE2` has unstable finite eigenvalues if `stable_unstable = true`.

The subpencil `Ai-λEi` is in a staircase form, with `Ai` nonsingular and upper triangular and `Ei` nilpotent and upper triangular.  The `nb`-dimensional vector `ν` contains the dimensions of the diagonal blocks of the staircase form  `Ai-λEi` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[i]-ν[i+1]` for `i = 1, 2, ..., nb` is the number of infinite elementary divisors of degree `i`  (with `ν[nb+1] = 0`).

The dimensions of the diagonal blocks are returned in `blkdims = (ni, n1, n2)`.   

(2) if `finite_infinite = true`, then

```
               | A1-λE1   *      *    |
    At - λEt = |    O   A2-λE2   *    |
               |    0     0    Ai-λEi |
```

where the `ni x ni` subpencil `Ai-λEi` contains the infinite elementary divisors,  the `n1 x n1` subpencil `A1-λE1` is with the pair `(A1,E1)` in a generalized Schur form, and the  `n2 x n2` subpencil `A2-λE2` is with the pair `(A2,E2)` in a generalized Schur form.  The pencil `A1-λE1` has unstable finite eigenvalues and `A2-λE2` has stable finite eigenvalues if `stable_unstable = false`, while `A1-λE1` has stable finite eigenvalues and `A2-λE2` has unstable finite eigenvalues if `stable_unstable = true`.

The subpencil `Ai-λEi` is in a staircase form, with `Ai` nonsingular and upper triangular  and `Ei` nilpotent and upper triangular.  The `nb`-dimensional vectors `ν` contains the dimensions of the diagonal blocks of the staircase form `Ai-λEi` such that `i`-th block has dimensions `ν[i] x ν[i]`.  The difference `ν[nb-j+1]-ν[nb-j]` for `j = 1, 2, ..., nb` is the number of infinite elementary  divisors of degree `j` (with `ν[0] = 0`).

The dimensions of the diagonal blocks are returned in `blkdims = (n1, n2, ni)`.   

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. 

The reduction is performed using rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The performed left orthogonal or unitary transformations are accumulated in the matrix `Q` if `withQ = true`.  Otherwise, `Q` is set to `nothing`.    The performed right orthogonal or unitary transformations are accumulated in the matrix `Z` if `withZ = true`.  Otherwise, `Z` is set to `nothing`.  
