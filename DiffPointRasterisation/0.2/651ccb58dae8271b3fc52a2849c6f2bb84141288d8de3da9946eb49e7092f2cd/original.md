```
raster(grid_size, points, rotation, translation, [background, out_weight])
```

Interpolate points (multi-) linearly into an Nd-array of size `grid_size`.

Before `points` are interpolated into the array, each point $p$ is first transformed according to

$$
\hat{p} = R p + t
$$

with `rotation` $R$ and `translation` $t$.

Points $\hat{p}$ that fall into the N-dimensional hypercube with edges spanning from (-1, 1) in each dimension, are interpolated into the output array.

The total weight of each point (`out_weight * point_weight`) is distributed onto the 2^N nearest pixels/voxels of the output array (according to the closeness of the voxel center to the coordinates of point $\hat{p}$) via N-linear interpolation.

# Arguments

  * `grid_size`: Tuple of integers defining the output dimensions
  * `points::AbstractVector{<:AbstractVector}`: A vector of same length vectors representing points
  * `rotation`: Either a single matrix(-like object) or a vector of such, that linearly transform(s) `points` before rasterisation.
  * `translation`: Either a single vector or a vector of such, that translates `points` *after* `rotation`. If `rotation` includes a projection, `translation` thus needs to have the same length as `rotation * points[i]`.
  * `background`: Either a single number or a vector of such.
  * `out_weight`: Either a single number or a vector (one per image) of such.
  * `point_weight`: A vector of numbers (one per point).

`rotation`, `translation`, `background` and `out_weight` can have an  additional "batch" dimension (by providing them as vectors of single parameters. The length of these vectors must be the same for all four arguments). In this case, the output array will have dimensionality +1 with an additional axis on last position corresponding to the number of elements in the batch. See [Raster a single point cloud to a batch of poses](@ref) for more details.

See also: [`raster!`](@ref)
