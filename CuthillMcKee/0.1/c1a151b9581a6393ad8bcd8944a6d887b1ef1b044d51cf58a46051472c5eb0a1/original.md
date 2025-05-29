```
 symrcm(A,[ rev, inv, warnunconnected])
```

Computes the Cuthill-McKee permutation of the structurally-symmetric sparse matrix `A`. The default is to compute the reverse permutation, i.e. `rev` defaults to `true`. Optionally, when `inv` is set to `true`, the permutation is inverted. Per default the warning displaying the number of unconnected regions in the graph is disabled, to enable, set `warnunconnected` to `true`. No checks are performed to ensure that the matrix is indeed structurally symmetric.
