```
abstract type AbstractCorrespondence
```

Method for determining the correspondence matching between blobs and measurements.

Supports functions `assign(c::AbstractCorrespondence, blobs, coordinates)`, `too_far(c::AbstractCorrespondence, blob, coordinate)`

# Subtypes

  * `HungarianCorrespondence`
  * `NearestNeighborCorrespondence`
