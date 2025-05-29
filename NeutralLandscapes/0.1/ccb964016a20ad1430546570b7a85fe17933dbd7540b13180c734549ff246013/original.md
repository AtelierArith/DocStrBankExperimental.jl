```
NearestNeighborCluster <: NeutralLandscapeMaker

NearestNeighborCluster(; p=0.5, n=:rook)
NearestNeighborCluster(p, [n=:rook])
```

Create a random cluster nearest-neighbour neutral landscape model with  values ranging 0-1. `p` sets the density of original clusters, and `n` sets the neighborhood for clustering (see `?label` for neighborhood options)
