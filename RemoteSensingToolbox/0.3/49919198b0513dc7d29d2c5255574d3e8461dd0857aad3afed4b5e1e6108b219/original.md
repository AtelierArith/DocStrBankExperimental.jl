```
inverse_pca(transformation::PCA, raster::AbstractRaster)
inverse_pca(transformation::PCA, signatures::Matrix)
```

Perform an inverse Principal Component Analysis (PCA) transformation to recover the original image.

# Parameters

  * `transformation`: A previously fitted PCA transformation.
  * `raster`: An `AbstractRaster` representing a previously transformed image.
  * `signatures`: An nxc matrix of previously transformed signatures where n is the number of signatures and c is the number of components.
