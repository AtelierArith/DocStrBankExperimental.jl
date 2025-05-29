```
landmark_isomap(coords, search=:knn, neigh=16, anchors=1500)
```

This function runs Landmark Isomap at 3-D points and returns a coordinate matrix with the unfolded points.

## Parameters:

  * `coords`  - coordinate matrix of the reference points.
  * `search`  - search type to build neighbors graph for Isomap (:knn for k-nearest neighbor or :radius for radius search)
  * `neigh`   - number of neighbors (for `search`=:knn) or radius distance (for `search`=:radius) to build neighbors graph for Isomap.
  * `anchors` - number of anchors/landmark points for the dimensionality reduction.
