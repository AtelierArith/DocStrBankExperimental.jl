```
unfold(to_unf, ref, unf_ref; optim=:default)
```

Unfold the input points `to_unf` based on points already unfolded `unf_ref` and their correspondent in the original space `ref`. Useful to unfold samples after the domain is already unfolded, for example. Returns a coordinate matrix with the unfolded points. Or a tuple of matrices if `to_unf` is a list of points.

## Parameters:

  * `to_unf`  - coordinate matrix with the points that will be unfolded
  * `ref`     - coordinate matrix with the reference points for unfolding
  * `unf_ref` - coordinate matrix with the unfolded reference points
  * `optim`   - additional parameters for optimization step; either :default or a NamedTuple with the keys shown below

### `optim` parameters:

*Default:* optim = (search=:knn, neigh=50, maxerr=5, nchunks=1)

  * `search`  - search type to optimize locally (:knn for k-nearest neighbor or :radius for radius search).
  * `neigh`   - number of neighbors (for search=:knn) or radius distance (for search=:radius) to local optimization.
  * `maxerr`  - the maximum accepted distortion for unfolding optimization.
  * `nchunks` - number of rounds of optimization.
