```
unfold(ref, to_unf, samps=nothing; isomap=:default, optim=:default)
```

Unfold the input points `to_unf` based on the reference points informed in `ref`. Returns a coordinate matrix with the unfolded points. Or a tuple of matrices if `to_unf` is a list of points.

## Parameters:

  * `to_unf`  - coordinate matrix with the points that will be unfolded
  * `ref`     - coordinate matrix with the reference points for unfolding
  * `isomap`  - additional parameters for isomap step; either :default or a NamedTuple with the keys shown below
  * `optim`   - additional parameters for optimization step; either :default or a NamedTuple with the keys shown below

### `isomap` parameters:

*Default:* isomap = (search=:knn, neigh=16, anchors=1500, reftol=0.01)

  * `search`  - search type to build neighbors graph for Isomap (:knn for k-nearest neighbor or :radius for radius search).
  * `neigh`   - number of neighbors (for search=:knn) or radius distance (for search=:radius) to build neighbors graph for Isomap.
  * `anchors` - number of anchors for landmark isomap
  * `reftol`  - distance to which reference points are considered duplicates

### `optim` parameters:

*Default:* optim = (search=:knn, neigh=50, maxerr=5, nchunks=4)

  * `search`  - search type to optimize locally (:knn for k-nearest neighbor or :radius for radius search).
  * `neigh`   - number of neighbors (for search=:knn) or radius distance (for search=:radius) to local optimization.
  * `maxerr`  - the maximum accepted distortion for unfolding optimization.
  * `nchunks` - number of rounds of optimization.
