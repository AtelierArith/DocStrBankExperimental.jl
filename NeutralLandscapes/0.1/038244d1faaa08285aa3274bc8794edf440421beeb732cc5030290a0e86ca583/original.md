```
DiscreteVoronoi <: NeutralLandscapeMaker

DiscreteVoronoi(; n=3) 
DiscreteVoronoi(n)
```

This type provides a rasterization of a Voronoi-like diagram. Assigns a value to each patch using a 1-NN algorithmm with `n` initial clusters. It is a `NearestNeighborElement` algorithmm with `k` neighbors set to 1. The default is to use three clusters.
