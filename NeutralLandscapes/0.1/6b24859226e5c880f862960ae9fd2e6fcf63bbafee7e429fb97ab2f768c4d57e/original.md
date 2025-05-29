```
NearestNeighborElement <: NeutralLandscapeMaker

NearestNeighborElement(; n=3, k=1)
NearestNeighborElement(n, [k=1])
```

Assigns a value to each patch using a k-NN algorithmm with `n` initial clusters and `k` neighbors. The default is to use three cluster and a single neighbor.
