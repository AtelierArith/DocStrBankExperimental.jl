```
klf_left_refineinf!(νi, M, N, Q, L; roff = 0, coff = 0, withQ = true)
```

Reduce the partitioned matrix pencil `M - λN` (`*` stands for a not relevant subpencil)

```
         [   *         *        *  ] roff
M - λN = [   0       Mi-λNi     *  ] ni
         [   0         0        *  ] rtrail
           coff       ni     ctrail
```

to an equivalent form `F - λG = Q1'*(M - λN)` using an orthogonal or unitary transformation  matrix `Q1`, such that the regular subpencil `Mi-λNi`, in staircase form,  with `Mi` nonsingular and `Ni` nillpotent and upper triangular, is transformed to obtain  `Mi` upper-triangular and preserve `Ni` upper triangular.  It is assumed that `Mi-λNi` has `nb` diagonal blocks and the `i`-th diagonal block has dimensions  `νi[i] x νi[i]`.

The performed orthogonal or unitary transformations are accumulated in `Q` (i.e., `Q <- Q*Q1`),  if `withQ = true`. 

The  matrix `L` is overwritten by `Q1'*L` unless `L = missing`. 
