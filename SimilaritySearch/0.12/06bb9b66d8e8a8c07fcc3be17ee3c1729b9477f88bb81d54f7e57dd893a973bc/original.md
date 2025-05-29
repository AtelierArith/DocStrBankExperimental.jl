```
SatNeighborhood(hfactor::Float32=0f0, nndist::Float32=1f-4)
```

New items are connected with a small set of items computed with a SAT like scheme (**cite**). It starts with `k` near items that are filterd to a small neighborhood due to the SAT partitioning stage.
