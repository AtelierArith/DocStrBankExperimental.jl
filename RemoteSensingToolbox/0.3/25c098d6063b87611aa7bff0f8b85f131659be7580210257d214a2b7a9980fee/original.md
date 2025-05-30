```
forward_pca(transformation::PCA, raster::Union{<:AbstractRaster, <:AbstractRasterStack}, components::Int)
forward_pca(transformation::PCA, signatures::Matrix, components::Int)
```

Perform a forward Principal Component Analysis (PCA) rotation while retaining only the specified number of components.

# Parameters

  * `transformation`: A previously fitted PCA transformation.
  * `raster`: The `AbstractRaster` or `AbstractRasterStack` on which to perform the PCA transformation.
  * `signatures`: An nxb matrix of signatures where n is the number of signatures and b is the number of bands.
  * `components`: The number of bands to retain in the transformed image or signatures.
