```
coarsen(f, L::SDMLayer, mask=(2, 2))
```

Coarsens a layer by collecting a sub-grid of size `mask`, and applying the function `f` to all non-empty cells within this mask. The core constraint is that `f` must take a vector and return a single element (and the size of the mask must be compatible with the size of the layer).
