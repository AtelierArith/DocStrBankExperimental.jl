```
blocks, M = blocksort(P::UncertainSS)
```

Returns the block structure of `P.Δ` as well as `P.M` permuted according to the sorted block structure. `blocks` is a vector of vectors with the block structure of perturbation blocks as described by μ-tools, i.e.

  * `[-N, 0]` denotes a repeated real block of size `N`
  * `[N, 0]` denotes a repeated complex block of size `N`
  * `[ny, nu]` denotes a full complex block of size `ny × nu`
