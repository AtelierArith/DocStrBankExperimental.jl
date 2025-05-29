```
eigvalscond(S::Schur,nsub::Integer) => Real
```

Estimate the reciprocal of the condition number of the `nsub` leading eigenvalues of `S`. (Use `ordschur` to move a subspace of interest to the front of `S`.)

See the LAPACK User's Guide for details of interpretation.
