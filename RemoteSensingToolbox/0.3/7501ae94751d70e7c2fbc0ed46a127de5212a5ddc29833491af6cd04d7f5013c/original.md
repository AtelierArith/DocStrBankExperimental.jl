```
forward_mnf(transformation::MNF, raster, components::Int)
forward_mnf(transformation::MNF, signatures::Matrix, components::Int)
```

Perform a forward Minimum Noise Fraction (MNF) rotation on the given raster or signatures, retaining only the specified number of components.

# Parameters

  * `transformation`: A previously fitted MNF transformation.
  * `raster`: The `AbstractRaster` or `AbstractRasterStack` on which to perform the MNF transformation.
  * `signatures`: An n x b matrix of spectral signatures where n is the number of signatures and b is the number of bands.
  * `components`: The number of bands to retain in the transformed image. All band numbers exceeding this value will be discarded.
