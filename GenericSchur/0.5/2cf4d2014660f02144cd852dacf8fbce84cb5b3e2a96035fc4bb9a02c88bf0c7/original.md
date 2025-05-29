```
eigvalscond(S::GeneralizedSchur, nsub) => pl, pr
```

compute approx. reciprocal norms of projectors on left/right subspaces associated w/ leading `nsub`×`nsub` block of `S`. Use `ordschur` to select eigenvalues of interest.

An approximate bound on avg. absolute error of associated eigenvalues is `ϵ * norm(vcat(A,B)) / pl`. See LAPACK documentation for further details.
