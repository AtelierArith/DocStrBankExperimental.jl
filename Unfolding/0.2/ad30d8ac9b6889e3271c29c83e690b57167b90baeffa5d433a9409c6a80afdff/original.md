```
getreference(blocks; axis=["X","Y","Z"])
```

Extract the mid-surface points that split the informed block model in two. Returns a coordinate matrix with the reference points for unfolding.

## Parameters:

  * `blocks` - coordinate matrix of the regular blocks centroids.
  * `axis`   - axis or list of axis that will be scanned to extract reference points. Defaults to ["X","Y","Z"].
