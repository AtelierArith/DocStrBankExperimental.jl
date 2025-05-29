```
klf_right_refineut!(ν, μ, M, N, Q, Z; ctrail = 0, withQ = true, withZ = true)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
         [ Mri-λNri  *   ] 
M - λN = [    0      *   ] 
                   ctrail
```

to an equivalent form `F - λG = Q1'*(M - λN)*Z1` using orthogonal or unitary transformation  matrices  `Q1` and `Z1`, such that the full row rank subpencil `Mri-λNri`, in staircase form ,  is transformed as follows: the full row rank diagonal blocks of `Mri` are reduced to the form `[0 X]`  with `X` upper triangular and nonsingular and the full column rank supradiagonal blocks of `Nri` are reduced to the form `[Y; 0]` with `Y` upper triangular and nonsingular.  It is assumed that `Mri-λNri` has `nb` diagonal blocks and the dimensions of the diagonal blocks   are specified by the `nb`-dimensional vectors `ν` and `μ` such that the `i`-th block has dimensions `ν[i] x μ[i]`.  

The performed orthogonal or unitary transformations are accumulated in `Q` (i.e., `Q <- Q*Q1`),  if `withQ = true` and `Z` (i.e., `Z <- Z*Z1`), if `withZ = true`. 
