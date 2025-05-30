```
inverse_mnf(transformation::MNF, raster::AbstractRaster)
inverse_mnf(transformation::MNF, signatures::Matrix)
```

Perform an inverse Minimum Noise Fraction (MNF) transformation to recover the original image or signatures.

# Parameters

  * `transformation`: A previously fitted MNF transformation.
  * `raster`: An `AbstractRaster` representing a previously transformed image. The number of bands should be less than or equal to that of the original image.
  * `signatures`: An n x p matrix of transformed signatures where n is the number of signatures and p is the number of retained components.
