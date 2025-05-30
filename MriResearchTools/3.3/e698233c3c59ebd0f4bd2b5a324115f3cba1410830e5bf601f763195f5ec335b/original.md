```
makehomogeneous(mag; sigma, nbox=15)
```

Homogeneity correction of 3D arrays. 4D volumes are corrected using the first 3D volume to obtain the bias field.

### Keyword arguments:

  * `sigma`: sigma size in voxel for each dimension for smoothing to obtain bias field. (mandatory)
  * `nbox`: Number of boxes in each dimension for the box-segmentation step.

Larger sigma-values make the bias field smoother, but might not be able to catch the inhomogeneity. Smaller values can catch fast varying inhomogeneities but new inhomogeneities might be created. The stronger the bias field, the more boxes are required for segmentation. With too many boxes, it can happen that big darker structures are captured and appear overbrightened.

Calculates the bias field using the `boxsegment` approach. It assumes that there is a "main tissue" that is present in most areas of the object. Published in [CLEAR-SWI](https://doi.org/10.1016/j.neuroimage.2021.118175).

See also [`getsensitivity`](@ref)
