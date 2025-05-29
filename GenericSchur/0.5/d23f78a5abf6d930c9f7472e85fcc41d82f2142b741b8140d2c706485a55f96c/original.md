```
subspacesep(S::Schur,nsub::Integer) => Real
```

Estimate the reciprocal condition of the separation angle for the invariant subspace corresponding to the leading block of size `nsub` of a Schur decomposition. (Use `ordschur` to move a subspace of interest to the front of `S`.)

See the LAPACK User's Guide for details of interpretation.
