```
spectraldistances_trace(usv::SVD; onrows=true, groups=nothing, alpha=1.0, q=0.5)
spectraldistances_trace(vecs, vals, groups)
```

calculates spectral residual within each partition of spectrum and each pair of taxa

returns matrix where rows are spectral partitions and columns are taxa:taxa pairs ordered as the upper triangle in rowwise order, or lower triangle in colwise order.

Args:

  * method: `spectraldistances_trace(vecs, vals, groups)`

      * vecs: either usv.U or usv.V matrix
      * vals: usv.S singular values vector
      * groups: usually calculated with `getintervals(usv.S; alpha=alpha, q=q)`
  * method: `spectraldistances_trace(usv::SVD; onrows=true, groups=nothing, alpha=1.0, q=0.5)`     

      * usv: SVD object
      * onrows: true/false switch to calculate spectral distance on rows (U matrix) or columns (V matrix).
      * groups: if nothing groups are calculated with `getintervals(usv.S; alpha=alpha, q=q)`,    otherwise they assume a vector of index ranges `[1:1, 2:3, ...]` to group `usv.S` with.
      * alpha: passed to `getintervals`
      * q: passed to `getintervals`
