```
NearestNeighborCorrespondence <: AbstractCorrespondence
```

Assign each blob the measurement that appears closest to the blob. This method can assign the same measurement to multiple blobs.

# Parameters

  * `dist_th=2`: maximum allowed Mahalanobis distance between a blob and a measurement
