```
klf_right_refineinf!(νi, M, N, Z, R; roff = 0, coff = 0, withZ = true)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
         [   *         *        *  ] roff
M - λN = [   0       Mi-λNi     *  ] ni
         [   0         0        *  ] rtrail
           coff       ni     ctrail
```

to an equivalent form `F - λG = (M - λN)*Z1` using an orthogonal or unitary transformation  matrix `Z1`, such that the regular subpencil `Mi-λNi`, in staircase form ,  with `Mi` nonsingular and `Ni` nillpotent and upper triangular, is transformed to obtain  `Mi` is upper-triangular and preserve `Ni` upper triangular.  It is assumed that `Mi-λNi` has `nb` diagonal blocks and the `i`-th diagonal block has dimensions  `νi[i] x νi[i]`.

The performed orthogonal or unitary transformations are accumulated in `Z` (i.e., `Z <- Z*Z1`),  if `withZ = true`. 

The  matrix `R` is overwritten by `R*Z1` unless `R = missing`. 
